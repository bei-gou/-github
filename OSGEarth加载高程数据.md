---

---

# OSGEarth加载高程数据

## osgEarth常见驱动

​	主要有：GDAL、MBTiles、TMS、WMS、XYZ、Microsoft Bing、Cesium Ion、ESRI Arcgis Server、MapboxGL等驱动。

​	常用驱动为GDAL、XYZ和TMS。

### GDAL支持的常见栅格影响格式说明

| Long Name                   | Short Name | Creation | Copy | Geo-referencing | Compiled by default             |
| --------------------------- | ---------- | -------- | ---- | --------------- | ------------------------------- |
| Arc/Info ASCII Grid         | AAIGrid    | NO       | Yes  | Yes             | Yes                             |
| ACE2                        | ACE2       | NO       | NO   | Yes             | Yes                             |
| Graphics Interchange Format | GIF        | NO       | Yes  | NO              | (internal GIF library provided) |
| **GeoTIFF File Format**     | **GTiff**  | Yes      | Yes  | Yes             | Built-in by default             |
| Web Map Services            | WMS        | NO       | Yes  | Yes             | libcurl                         |
| ASCII Gridded XYZ           | XYZ        | NO       | Yes  | Ye              | Built-in by default             |
| ZMap Plus Grid              | ZMAP       | NO       | Yes  | Ye              | Built-in by default             |

上述为详细格式说明地址。加粗的为主要使用格式。

```HTML
<a href=''>[Raster drivers — GDAL documentation](https://gdal.org/drivers/raster/index.html)</a>
```

## URL

​	URL（Uniform Resource Locator）是指统一资源定位符，是用于完整地描述Internet上网页和其他资源的地址的一种标识方法，也被称为“网址”。在Internet上所有资源都有一个独一无二的URL地址，我们可以通过在地址栏中输入URL实现对资源的访问。

​	URL通常由多个部分组成，包括协议类型（如HTTP、HTTPS）、主机名（域名或IP地址）、路径（资源在主机上的位置）以及可选的查询参数（用于传递额外的信息）。通过URL，用户可以方便地访问和定位到特定的网络资源。

## osgEarth常见驱动所用文件格式

影像图层：基于栅格数据的地图制图集合。栅格数据是通常用于存储遥感设备捕获的影像和其他信息的像元格网。 影像图层可以动态显示，也可以作为缓存的图像切片进行预渲染。

高程图层：高程表面图层是一个复合图层，表示地表或自定义表面。用于定义地图或场景范围内的高度值。 高程表面图层包含一个或多个为表面贡献高度值的高程源图层 。

### shp文件

​	shp文件是一种空间数据开放格式，由美国环境系统研究所公司（ESRI）开发。它主要用于描述几何体对象，如点、折线与多边形，并能保存几何图形的位置及相关属性。

​	shp文件是矢量图形格式，能够保存几何图形的位置及相关属性。shp文件由多个文件组成，包括.shp（图形格式）、.shx（图形索引格式）和.dbf（属性数据格式）文件。这些文件必须位于同一个目录中，并且它们必须具有相同的文件名前缀。

​	shp文件在地理信息系统中具有重要的应用价值，它们可以在ESRI与其他公司的产品之间进行数据互操作，是地理信息软件界的一个开放标准。例如，shp文件可以用于描述河流、湖泊等空间对象的几何位置，以及存储这些空间对象的属性信息。

### xml文档

1.<SRS>EPSG:4326</SRS>`：这是定义坐标系统的空间参照系统（Spatial Reference System），EPSG:4326是指WGS84坐标系统，广泛用于GPS和互联网地图服务等。

2.<BoundingBox minx="-180.000000" miny="-90.000000" maxx="180.000000" maxy="90.000000"/>`：这是定义瓦片覆盖范围的边界框，这里设置的范围是整个地球的表面。

3.<Origin x="-180.000000" y="-90.000000"/>`：这是定义地图原点的坐标，也就是地图开始的位置。这里设置的原点坐标也是基于WGS84坐标系统。

4.<TileFormat width="256" height="256" mime-type="image/jpeg" extension="jpeg"/>`：这是定义瓦片的格式，包括瓦片的宽度和高度（这里是256x256像素），以及瓦片图像的MIME类型（这里是JPEG图像）和扩展名（这里是.jpeg）。

5.TileSets：这里面提供了一组瓦片集的链接和属性，例如每个瓦片集的href(用于获取瓦片的URL)、units-per-pixel(每个像素单位的单位长度)和order(瓦片集的顺序)。

6.DataExtents：每个DataExtents定义了一个地理空间数据的范围，包括最小经纬度(minx,miny)和最大经纬度(maxx,maxy)以及数据的最低级别(minlevel)和最高级别(maxlevel).

## 根、组、叶节点

​	根节点：树的顶部节点，其他节点都是从根节点开始通过一条唯一的路径到达的。

​	组节点：拥有子节点的节点称为组节点或内节点。这些节点位于根节点和叶节点之间。

​	叶节点：没有子节点的节点称为叶节点或外节点。叶节点是树的末端，不存在其他节点指向它们

## Earth格式文件说明

### 地图Map，MAP是根节点。

```HTML
<map name  = "my map"
     type  = "geocentric"
  version  = "2">
</map>
```

| 属性    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| name    | 名字节点，不影响渲染。                                       |
| type    | 属性可以是geocentric和projected两种模式，分别对应地心坐标系和平面投影坐标系,默认是地心坐标模式。 |
| version | Version是osgEarth的主版本号，必须有版本号，默认是“2”，这样设置可以加载旧版本文件。也有为“1”的情况。 |

### 地图选项 Map Options

这些选项控制地图模型以及整个地图渲染过程涉及的参数。

<map>
</map>
	<options lighting           = "true"
	 elevation_interpolation    = "bilinear"
	    overlay_texture_size    = "4096"
	        overlay_blending    = "true"
	overlay_resolution_ratio    = "3.0">
| 属性                     | 说明                                                         |
| ------------------------ | ------------------------------------------------------------ |
| lighting                 | 是否允许照明着色器影响贴图。                                 |
| elevation_interpolation  | 重采样高程源数据时要使用的算法有{nearest(最近相邻)、average(相邻值平均值)、bilinear(两轴线性插值)、triangulate(interp遵循三角坡度)}。 |
| overlay_texture_size     | 设置要用于覆盖的纹理大小(投影纹理)。                         |
| overlay_blending         | 覆盖几何体是否在覆盖期间与地形混合(投影纹理)                 |
| overlay_resolution_ratio | 对于覆盖几何体，是指靠近摄影机的投影纹理的分辨率与远离摄影机的分辨率的比率。增大该值可改善靠近摄影机的外观，同时牺牲更远几何体的外观。注意：如果你使用一个支持侧翻的摄影机操纵器，你可能需要将其设置为1.0；否则你将得到覆盖物！ |

### 地形选项 Terrain Options

这些选项控制地形曲面的渲染。

```
<map\>
    <options>
        <terrain driver        = "rex"
                 lighting      = "true"
        min_tile_range_factor  = "6"
                 first_lod     = "0"
                 blending      = "false"
                 color         = "#ffffffff"
                 title_size    = "17"
              normalize_edges  = "false"
         compress_normal_maps  = "false"
                 normal_maps   = "true"
           min_expiry_frames   = "0"
            min_expiry_time    = "0" >
```

|         属性          | 说明                                                         |
| :-------------------: | ------------------------------------------------------------ |
|        driver         | 要加载的地形引擎插件类型。 默认是“rex”。请参阅“驱动程序”参考指南，了解每个插件的特定属性。 |
|       lighting        | 地形是否接受照明（如果存在）。默认是：true                   |
| min_tile_range_factor | 最小瓦片范围因子：对于某个大小的瓦片，想要能看到时候的最小距离。例如某个瓦片半径是10KM，这个MTRF因子为7，那么瓦片在大约70公里时候可见。默认是6.0。 |
|       first_lod       | 地形图上将会显示瓦片的最低的级别。如果在更低的 LOD级别上就不会显示瓦片。 |
|       blending        | 这个值设置为true可以让GL渲染地表以下的地理环境，可以让地球变得部分透明，这样就可以方便的看到地下的一些物理。 |
|       tile_size       | 地形瓦片的尺寸。每个瓦片都将有 `tile_size * tile_size`个顶点。默认是17。 |
|    normalize_edges    | 沿地形瓦片的边缘计算法线向量，以便从一个瓦片到另一个瓦片的照明会更平滑。默认设置为false |
|      normal_maps      | 是否生成和使用法线贴图代替几何体法线。法线贴图与照明一起使用，创建的地形会比单独使用三角形表示的分辨率更高。默认值取决于引擎。 |
| compress_normal_maps  | 是否在将法线贴图发送到GPU之前压缩法线贴图。您必须在OpenSceneGraph 库BUILD时候，内置NVIDIA纹理工具图像处理器插件。默认值为false |
|   min_expiry_frames   | 地形瓦片在可以考虑过期之前没有看到的帧数。默认值为0          |
|    min_expiry_time    | 地形瓦片在可以考虑过期之前未被剔除的秒数。默认值为0          |

### 图层Image Layer

图层：覆盖在地球几何体上的光栅图像。

```
<map>
    <image name          = "my image layer"
           driver        = "gdal"
           nodata_image  = "http://readymap.org/nodata.png"
           opacity       = "1.0"
           min_range     = "0"
           max_range     = "100000000"
       attenuation_range = "0"
           min_level     = "0"
           max_level     = "23"
         min_resolution  = "100.0"
         max_resolution  = "0.0"
         max_data_level  = "23"
           enabled       = "true"
           visible       = "true"
           shared        = "false"
         shared_sampler  = "string"
         shared_matrix   = "string"
           coverage      = "false"
           min_filter    = "LINEAR"
           mag_filter    = "LINEAR"
           blend         = "interpolate"
           altitude      = "0"
     texture_compression = "none" >
     
        <cache_policy>
        <proxy>
```

| 属性                          | 说明                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| name                          | 名字                                                         |
| driver                        | 用于为此层创建瓦片的插件。请参阅驱动程序参考指南，了解每个插件的特定属性。 |
| nodata_image                  | 如果数据源没有数据，则用此URI地址的图片。如果osgEarth使用了此图像，则说明数据源没有找到数据。 |
| opacity                       | 图层的不透明度： [0..1].                                     |
| min_range/max_range           | 到摄像机的最小(大)可见距离（米），如果距离太小(大)了，则不可见。 |
| attenuation_range             | 向最小范围或最大范围渲染的距离。（文本或图标不支持，仅支持几何图形） |
| min_level/max_level           | 细节的最小(大)可见级别。                                     |
| min_resolution/max_resolution | 绘制瓦片的最小(大)源数据分辨率。源数据是几个单位，这里每像素就是几个单位。 |
| max_data_level                | 此图像层可以使用新源数据的最大详细级别。通常驱动会报告这些信息。但你可能希望自己限制一下。这对于一些没有分辨率限制的驱动程序来说尤其如此，例如光栅化驱动程序（聚集体）。 |
| enabled                       | 是否在地图中包含此图层。您只能在加载时设置它；这只是在地球文件中“注释掉”图层的一种简单方法。 |
| visible                       | 图层是否可见。                                               |
| shared                        | 为该层生成辅助的专用采样器，以便自定义着色器可以全局访问它。 |
| shared_sampler                | 对于共享图层，将在GLSL代码中使用的采样器统一名称。           |
| shared_matrix                 | 对于共享图层，将在GLSL代码中使用的纹理矩阵的统一名称，您可以使用该名称访问上面shared_sampler的正确纹理坐标。 |
| coverage                      | 指示这是一个覆盖层，即，用特定语义传递离散值的层。例如，“土地利用”层，其中每个像素都有一个值，该值指示该区域是否为草地、沙漠等。将一个层标记为覆盖将禁用任何插值、滤波或压缩，因为这些将损坏GPU上的采样数据值。 |
| min_filter                    | 用于此层的OpenGL纹理缩小过滤器。选项包括：NEAREST, LINEAR, NEAREST_MIPMAP_NEAREST, NEAREST_MIPMIP_LINEAR, LINEAR_MIPMAP_NEAREST, LINEAR_MIPMAP_LINEAR |
| mag_filter                    | 用于此层的OpenGL纹理放大过滤器。选项同上                     |
| texture_compression           | “auto” 表示自动在GPU上压缩纹理; “none” 禁用. “fastdxt” 使用 FastDXT 算法实时DXT 压缩器 |
| blend                         | “modulate”将像素与帧缓冲区相乘；“interpolate”基于alpha（def）与帧缓冲区混合 |
| altitude                      | 渲染图层的海拔。可以使用这个参数在地面以上渲染天气或者云层，再比如, 一个视觉助手. 默认是0 |

### 高程层 Elevation Layer

高程图层为地形引擎提供高度地图栅格。osgEarth引擎将把所有的高程数据合成一个单一的高度图，并使用它来构建地形图块。

```
<map>
    <elevation name            = "text"
               driver          = "gdal"
               min_level       = "0"
               max_level       = "23"
               min_resolution  = "100.0"
               max_resolution  = "0.0"
               enabled         = "true"
               offset          = "false"
               nodata_value    = "-32768"
               min_valid_value = "-32768"
               max_valid_value = "32768"
               nodata_policy   = "interpolate" >
```

| 属性                            | 说明                                                         |
| ------------------------------- | :----------------------------------------------------------- |
| name                            | 同上                                                         |
| min_level/max_level             | 同上                                                         |
| min_resolution/max_resolution   | 同上                                                         |
| enabled                         | 同上                                                         |
| offset                          | 指示此图层中的高程值是相对偏移，而不是真实地形高度采样。     |
| nodata_policy                   | 如何处理“无数据”值。默认值为“插值”，它将插值相邻值以填充孔洞。将其设置为“msl”，将“无数据”样本替换为当前海平面值。 |
| nodata_value                    | 看到这个值就是没有数据。                                     |
| min_valid_value/max_valid_value | 如果任何小(大)于此值的，都视为无数据。                       |

### 模型层 [Model](https://so.csdn.net/so/search?q=Model&spm=1001.2101.3001.7020) Layer

把3维的模型也作为一个图层来渲染绘制。

```
<map>
    <model name    = "my model layer"
           driver  = "simple" >
```

说明与属性同上。

模型层还允许您定义剪切蒙版（cut-out [mask](https://so.csdn.net/so/search?q=mask&spm=1001.2101.3001.7020)）。地形引擎将在地形表面上切割一个孔，并与您提供的边界几何图形相匹配。可以使用工具osgearth_boundarygen创建这样的几何体。

如果您有一个外部地形模型，并且希望将其插入到osgEarth地形中，这将非常有用。

模型必须与地形处于同一坐标系中。

```
<map>
    <model ...>
        <mask driver="feature">
            <features driver="ogr">
                ...
```

蒙版可以将任何面要素作为输入。可以使用内嵌几何图形指定遮罩几何图形。

```
<features ...>
    <geometry>POLYGON((120 42 0, 121 41 0, 121 40 0))</geometry>
```

或者，你可以使用shapefile或其他特征数据，这时会使用指定的驱动加载。

### 简况 Profile

告诉osgEarth空间参考系统、地理空间范围和它应该用于渲染瓦片的平铺方案。

```
<profile srs    = "+proj=utm +zone=17 +ellps=GRS80 +datum=NAD83 +units=m +no_defs"
	 	或者prog   =  “latlong +ellps=WGS84 +datum=WGS84”
         vdatum = "egm96"
         xmin   = "560725.500"
         xmax   = "573866.500"
         ymin   = "4385762.500"
         ymax   = "4400705.500"
         num_tiles_wide_at_lod_0 = "1"
         num_tiles_high_at_lod_0 = "1">
```

| 属性                 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| srs                  | 地图的空间参考系。这可以是 WKT 字符串、EPSG 代码、PROJ4 初始化字符串或股票配置文件名称。有关详细信息，请参阅空间参考。 |
| prog                 | 空间参考系统初始化字符串，该字符串的值可以参考PROJ4或WKT，上面是用PROJ4定义的WGS84投影 profile，srs以及作用范围的定义同样适用于平面投影模式 |
| vdatum               | 截面梁的垂直基准面，用于描述如何处理 Z 值。有关详细信息，请参阅空间参考。 |
| xmin/xmax/ymin/ymax  | 地图的地理空间范围。这些单位是由上面的 SRS 定义的单位（通常为投影地图的米，地心地图的度）。 |
| num_tiles_*_at_lod_0 | 磁贴层次结构最顶层的大小。两个方向的默认值均为“1”。（可选）  |

### Cache

为瓦片数据设置缓存。

```
<cache driver = "filesystem"
       path   = "c:/osgearth_cache" >
```

| 属性   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| driver | 缓存使用的驱动方式, `filesystem` 或者 leveldb。              |
| path   | 相对路径，或者绝对路径，缓存目录或者文件。文件缓冲数据存放.db目标文件，适用于sqlite3，指定数据库文件名 |
|        |                                                              |

### CachePolicy

确定“给定元素”与“配置的缓存”交互的策略。

```
<cache_policy usage = "no_cache">
<cache type         = "tms/"sqlite3"/"tilecache" >
<cache_only         = "false">
```

| 属性       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| usage      | 缓存策略                                                     |
|            | read_write:如果配置就使用。默认值是这个。                    |
|            | cache_only:仅仅从缓存读数据，忽略数据源数据；离线渲染时候有用。 |
|            | no_cache:忽略缓存，仅仅从数据源加载。                        |
| max_age    | 其中usage可以换成max_age。单位是秒，早于此值 的缓存都视为超时过期了。 |
| cache type | 定义数据缓冲机制，缓冲类型有三种，tms、sqlite3以及tile cache，默认是tms |
| cache_only | 如果将cache_only设为true，osgEarth将只加载缓冲的数据，不加载任何非缓冲的数据，默认是false。 |

### 网络设置Proxy Settings

Proxy 设置可以让大家设置数据的代理服务器，比如科学上网。

```
<proxy host     = "hostname"
       port     = "8080"
       username = "jason"
       password = "helloworld" >
```

### Libraries

预先加载某些库。

```
<libraries>a</libraries>
<libraries>a;b;c;d;e</libraries>
```

多个库可以使用分号 ‘;’ 来分隔。
在osg库路径中搜索库，库名需要遵循osg nodekit库名约定（后缀加上osg库版本号）

### 其他

1.缓冲目标文件类型,适用于tms以及tilecache两种类型，如果没有指定类型，将默认用影像数据或高程数据的类型。

2.tms类型，仅适用于tms类型，注意如果该类型是google，索引就是反的。

3.缓冲文件最大值，单位是MB，不知道该属性是否只是适用于sqlite3，有待确定

4.坐标投影属性，该属性相当于渲染数据的地理空间上下文，它决定了系统以哪种方式将世界坐标数据投影到屏幕像素。为了正确渲染影像数据以及高程数据,osgEarth需要知道数据源的profile以及渲染时的profile以进行必要的转换。

5.由于WGS84比较著名，所以可以用下面的简化方式代替上面的定义

6.另外一个著名的球体投影就是墨卡托投影(yahoo、google、微软、openstreetmap都是用的这种投影方式)，这种投影方式的优点是可以在任何纬度或者预留区域正确地显示文本信息，可以用下面的简化方式定义

7.定义垂直空间参考系统，相当于垂直高程大地基准

8.定义如何加载地形数据(数据加载策略)，可以定义加载模式mode，分为standard(标准加载模式)、sequential(顺序加载模式)以及preemptive(优先级加载模式)，默认是标准加载模式，preemptive加载模式不同于顺序加载模式，当需要加载最高级瓦片时需要从最低级开始逐层加载，而preemptive模式可以直接跳过中间级直接加载最高级，同时还可以设定不同数据的加载优先级，比如可以设定优先加载影像数据而后加载高程数据等，这样可以在视觉上得到优化处理。此外还可以指定加载数据时每个CPU创建的线程数量(loading_threads_per_core)或者加载数据使用的总的线程数量(loading_threads)，以及编译地形数据即构建地形瓦片所使用的线程数量(compile_threads)，注意，加载数据时每个CPU创建的线程数量和加载数据使用的总的线程数量不能同时指定，只能指定其中一种

9.定义多个影像数据叠加时如何集成最终的影像数据,一共有四种方式，分别是auto(自动)、multitexture(多重纹理)、texture_array(纹理数组)、multipass(多通道)，默认是auto方式，这种方式是系统自动选择一种纹理组合方法，它首先检测硬件所支持的各种方法然后选择第一种。Multitexture方式会为每个影像层指定它自己的影响纹理单元然后通过GPU进行组合，允许的最大纹理层的数量要受GPU的限制，texture_array是使用一个二维纹理数组通过GPU进行组合，multipass方式是通过创建多个渲染通道进行纹理的组合，这种方式没有纹理层数量的限制，但会影像系统的性能，因为它要给每个纹理层创建一个渲染通道

10.定义地形瓦片分割的最大层数

11.定义瓦片数据的采样率，通过设定不同的采样率以得到不同精细程度的地形瓦片，默认是1.0，详情可参考osgTerrain

12.定义地形瓦片边缘率，osgTerrain会在不同的瓦片之间绘制边缘以防止不同的瓦片之间出现缝隙，该值默认是0.02，如果该值太小，在不同瓦片之间就可能会出现缝隙，如果太大，可能会造成不必要的渲染而影响系统的渲染性能，对于高度变化比较大的地形或者是做了高程夸张的地形可以尽量将该值设的大一些，以免出现缝隙

13.定义高程夸张系数，默认是1.0，也就是正常渲染高程的真实高度

14.定义边缘缓冲率，就是地形瓦片的延展率，比如将地形做镶嵌或者重投影时为了能够准确覆盖到所有的瓦片数据需要将瓦片范围进行适当的放宽，如果设定0.2，放宽的倍数就是1.02

15.指定该影像数据使用的profile，给该数据源指定profile后将覆盖map的全局profile，默认情况下，影像驱动器会自动判断数据源应该使用的profile，如果我们觉得驱动器无法自动判断得到数据源的profile时就要手动指定profile

16.复合驱动器，可以将多个影像数据源(可以使用各自不同的驱动器)复合成一个逻辑图层，其实是一个伪装的驱动器，不是真实的驱动器

17.GDAL驱动器，使用该驱动器，指定源数据url时可以指定文件也可以指定某个目录(不必将所有的文件都打包成一个文件)，如果指定了目录，还可以指定要加载该目录下某些类型的文件(通过指定扩展名)，此外，如果指定的是目录，系统递归遍历该目录下的所有文件将要加载的文件生成一个逻辑图层，需要注意的是，该目录下所有的数据必须是统一的坐标系统以及同样的波段和波段插值；基于性能的考虑，最好对源数据预先进行分块分级处理以及坐标重投影预处理，这样可以大大提高系统在运行时的性能。如果系统读取到的源数据与运行时要求的投影方式不匹配，系统就会在运行时对数据进行重投影，这样就会降低系统性能，如果想在这种情况下提高系统性能，可以让系统缓存重投影后的数据

18.通过指定目录的方式加载高程数据示例

19.对于高程数据，最好将tile_size设置为32或者64，默认情况下tile_size的值是256

```
1.<format>jpg</format>
2.<tms_type>google</tms_type>
3.<max_size>300</max_size>
  </cache>
4.<profile name=”myProfile”>
5.<profile>global-geodetic</profile>
6.<profile>global-mercator</profile>
7.<vsrs>egm96-meters</vsrs>
  </profile>
8.<loading_policy mode=”preemptive” loading_threads_per_core=”3” compile_threads=”2” ></loading_policy>
9.<compositor>auto/multitexture/texture_array/multipass</compositor>
10.<max_lod>10</max_lod>
11.<sample_ratio>1.2</sample_ratio>
12.<skirt_ratio>0.05</skirt_ratio>
13.<vertical_scale>2.0</vertical_scale>
14.<edge_buffer_ratio>0.02</edge_buffer_ratio>
   </terrain>
15.<profile>global_geodetic</profile>
16.<image name="grouped layer" driver="composite">
   <image name="component 1" driver="tms">
   ...
   </image>
   <image name="component 2" driver="wms">
   ...
   </image>
   ...
   </image>
17.<cache reproject_before_caching="true">
   <path>/files/my_cache_folder</path>
   </cache>

   <image name="boston_inset" driver="gdal">
   <url>../data/boston-inset.tif</url>
   <tile_size>256</tile_size>
   </image>
18.<heightfield name="terrain" driver = "gdal">

   <!--To load the files in a directory, just point the URL to a directory instead of a file-->
   <url>..\data\terrain</url>
   <!--Tell the GDAL driver to just look for tifs. Other files types will be ignored.-->
   <extensions>tif</extensions>
19.<tile_size>32</tile_size>
   </heightfield>
```

# Earth文件例子

osgEarth 使用熟悉的 **Map/Layer** 范式来组织数据。**Map** 由一组**图层**组成。渲染器从下到上逐个绘制每个可见图层，以显示最终场景。[您可以在此处查看所有不同的图层类型]（layers.md）。

**Earth 文件**是一个 XML 文件，用于描述 osgEarth 中**Map**的内容。

### 第一个 Earth File

这是一个非常简单的 earth 文件，您可以在存储库的“tests”文件夹中找到它：

```xml
<Map name="Hello, World">
    <GDALImage name="World imagery">
        <url>../data/world.tif</url>
    </GDALImage>
</Map>
```

此地图包含一个指向本地 GeoTIFF 文件的图层。在本例中，该位置相对于地球文件本身的位置。您也可以通过运行osgEarth命令行之一来查看此映射

```
osgearth_toc simple.earth
```

### 使用多图层

您可以根据需要向**地图**添加任意数量的图层。下面是一个名为“hires-inset.earth”的示例

```xml
<Map name="Hello, World">    
    <!-- Worldwide image -->
    <GDALImage name="World">
        <url>../data/world.tif</url>
    </GDALImage>

    <!-- Higher resolution inset of Boston -->
    <GDALImage name="Boston">
        <url>../data/boston-inset-wgs84.tif</url>
    </GDALImage>
    
    <!-- Higher resolution inset of New York City -->
    <GDALImage name="New York">
        <url>../data/nyc-inset-wgs84.tif</url>
    </GDALImage>
</Map>
```

在这种情况下，osgEarth将首先绘制“World”图层，然后是“Boston”，最后是“New York”。我们还在其中穿插了一些 XML 注释。

### 添加高程数据

现在，让我们添加一些高度字段数据，也称为 **DEM** 或数字高程模型：

```xml
<Map name="ReadyMap">
    <TMSImage name="ReadyMap 15m Imagery">
        <url>http://readymap.org/readymap/tiles/1.0.0/7/</url>
    </TMSImage>

    <TMSElevation name="ReadyMap 90m Elevation">
        <url>http://readymap.org/readymap/tiles/1.0.0/116/</url>
        <vdatum>egm96</vdatum>
    </TMSElevation>

    <Viewpoints>
        <Viewpoint name="San Francisco, California">
            <heading>10/heading>
            <height>4500.0</height>
            <lat>37.5581</lat>
            <long>-122.334</long>
            <pitch>-34</pitch>
            <range>78000</range>
        </Viewpoint>
    </Viewpoints>
</Map>
```

这里发生了几件事：首先，我们看到一个“TMSImage”图层，该图层通过 Internet 从切片地图服务图层加载影像。然后，我们有一些来自同一台服务器的 90m 数字高程数据。

最后，您可以看到一个“视点”图层。这根本不是可见的图层！相反，如果存储数据 - 在本例中，是用户可以导航到的一组预设视点。osgEarth将各种数据存储为**层**，并非所有数据都可见。不可见图层可以出现在地图中的任何位置。它们的顺序或外观无关紧要。

### 绘制矢量特征

最后，让我们看一些矢量特征数据。这是点、线和面形式的 GIS 数据。osgEarth有多种方法来显示这些数据，但现在让我们保持简单。你可以在 'feature_rasterize.earth' 中找到这个：

```xml
<Map name="Rasterize Vectors">
    <xi:include href="readymap_imagery.xml"/>
    
    <OGRFeatures name="world-data">
        <url>../data/world.shp</url>
    </OGRFeatures>
    
    <FeatureImage name="Countries" opacity="0.75">
        <features>world-data</features>
        <styles>        
            <style type="text/css">
                default {
                    fill:          #ff7700;
                    stroke:        #ffff00;
                    stroke-width:  5km;
                }
            </style>
        </styles>
    </FeatureImage>  
</Map>
```

首先，我们看到使用 '<xi：include>'，这是一个方便的 XML 指令，用于内联包含另一个 XML 文件。我们用它来获取我们的图像。

接下来是“OGRFeatures”层。这是一个数据层 - 它不会直接渲染 - 而只是指向我们存储在本地的 ESRI Shapefile。

最后，“FeatureImage”层指向数据层，并描述如何使用“StyleSheet”绘制数据层。



# OsgEarth贴图

在对地球进行贴图时，需要注意输入文件的图像格式，下载文件需要是Geo-TIFF的样式，文件下载成功后的文件格式为*.tif。*只有这样的贴图才能被识别，原因是GDAL驱动器，无法识别单纯的.tif文件。下面是下载网站和下载文件例子。

![image-20231124172056166](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20231124172056166.png)

```
https://visibleearth.nasa.gov/collection/1484/bl?page=1
```

