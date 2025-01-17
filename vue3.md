# 一、安装Node.js

Node.js的安装过程没有特别的注意事项，整个安装过程中都可以**不必修改任何内容**，直至其自动安装完成。

<img src="C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240918093748416.png" alt="image-20240918093748416" style="zoom:200%;" />

![image-20240918093825731](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240918093825731.png)

![image-20240918093833886](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240918093833886.png)

![image-20240918093841035](C:\Users\1\AppData\Roaming\Typora\typora-user-images\image-20240918093841035.png)

# 二、安装vue3

## 建议

用pnmp包管理器创建项目，优势：比同类工具 快两倍左右，节省磁盘空间

安装方式：

```cmd
npm install -g pnpm
```

创建项目：

```vscode
pnpm create vue
```

```cmd
pnpm install
pnpm dev
pnpm format//是用来格式化的，通过借助prettier的配置，对内容格式化
```



## 不建议！！！

管理员权限打开cmd

```cmd
npm init vue@latest 
```

根据提示进行按需安装依赖包，同时创建工程

## Eslint配置代码风格

配置文件 .eslintrc.cjs

```vue
rules: {
    'prettier/prettier': [
      'warn',
      {
        singleQuote: true, //单引号
        semi: false, //无分号
        printwidth: 80, //每行宽度至多80字符
        trailingComma: 'none', //不加对象|数组最后逗号
        endOfLine: 'auto' //换行符号不限制（win mac 不一致）
      }
    ],
    'vue/multi-word-component-names': [
      'warn',
      {
        ignores: ['index'] //vue组件名称多单词组成（忽略index.vue）
      }
    ],
    'vue/no-setup-props-destructure': ['off'], //关闭props解构的校验
    //添加未定义变量错误提示，create-vue@3.6.3关闭
    'no-undef': 'error'
  }
```

## 配置代码检查工作流

提交前做代码检查！！！

1.初始化git仓库，执行即可

```git
git init
```

2.初始化husky工具配置，执行一下即可

```jsx
pnpm dlx husky-init && pnpm install
```

3.修改.husky/pre-commit文件

```
pnpm lint
```

## lint-staged配置/暂存区eslint校验

1.

```
pnpm i lint-staged -D
```

2.package.json配置lint-staged命令

```
"lint-staged": {
	"*.{js,ts,vue}": [
		"eslint --fix"
	]
}
//在scripts中加入
  "scripts": {
    "lint-staged": "lint-staged"
  }
```

3.husky/pre-commit文件修改

```
pnmp lint-staged
```

## 路由初始化

1.创建路由实例由createRouter实现

2.路由模式：history模式使用createWebHistory()；hash模式使用createWebHashHistory()

3.参数是基础路径，默认/

在vue3 CompositionAPi中

1.获取路由对象

```
const router = useRouter()
```

2.获取路由参数route

```
const route = useRoute()
```

## 引入Element-Plus

1.安装

```
pnpm install element-plus
pnpm install -D unplugin-vue-components unplugin-auto-import

// vite.config.ts
import { defineConfig } from 'vite'
import AutoImport from 'unplugin-auto-import/vite'
import Components from 'unplugin-vue-components/vite'
import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'

export default defineConfig({
  // ...
  plugins: [
    // ...
    AutoImport({
      resolvers: [ElementPlusResolver()],
    }),
    Components({
      resolvers: [ElementPlusResolver()],
    }),
  ],
})

引入图标
pnpm i @element-plus/icons-vue
```

2.配置按需导入

```
https://element-plus.org/zh-CN/guide/quickstart.html
```

3.使用组件

## Pinia构建用户仓库和持久化

```
1.安装
pnpm add pinia-plugin-persistedstate -D
2.使用main.js
import persist from 'pinia-plugin-persistedstate'

app.use(createPinia().use(persist))
3.配置store/user.js
import { defineStore } from 'pinia'
import { ref } from 'vue'

//用户模块
export const useUserStore = defineStore(
'big-user',
() => {
	const token = ref('')//定义token
	const setToken = (t) => (token.value = t) //设置token
	
	return { token, setToken }
	},
	{
		persist: ture //持久化
	}
)
```



## axios配置

```
1.安装
pnpm add axios
2.新建utils/request.js封装axios模块
import axios from 'axios'

const baseURL = 'http://big-event-vue-api-t.itheima.net'

const instance = axios.create({
  //TODO 1.基础地址 超时时间
})
instance.interceptors.request.use(
(config) => {
//TODO 2.携带token
return config
},
(err) => Promise.reject(err)
)

instance.interceptors.request.use(
(res) => {
//TODO 3.处理业务失败
//TODO 4.摘取核心响应数据
return res
},
(err) => {
//TODO 5.处理401错误
Promise.reject(err)
}
)

export default instance 
```



# 三、vue笔记

响应式数据

reactive()：接受对象类型数据的参数传入并返回一个响应式的对象

ref()：接收简单类型或者对象类型的数据传入并返回一个响应式的对象



模板引用：通过ref表示获取真实的dom对象或者组件实例多选

1.调用ref函数生成一个ref对象    2.通过ref标识绑定ref对象到标签

