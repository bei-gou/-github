方法一：

安装

```
npm install xlsx file-saver --save
```





```




// 处理每行数量变化的函数
const handleNumChange = (value: number, row: any) => {
  row.Number = value // 只修改当前行的 num
  row.SumPrice = row.Price * row.Number // 重新计算该行的总价
}
// 处理每行单价变化的函数
const handlePriceChange = (value: number, row: any) => {
  row.Price = value // 只修改当前行的 Price
  row.SumPrice = row.Price * row.Number // 重新计算该行的总价
}
// 监听每行数量和单价的变化（可选全局监听）
// 支付
const payMoney = ref([])
dialogData.value.forEach((row) => {
  watch(
    () => [row.Number, row.Price],
    () => {
      row.SumPrice = row.Price * row.Number // 实时更新每行的总价
      console.log(`Number: ${row.Number}, Price: ${row.Price}, SumPrice: ${row.SumPrice}`)
    }
  )
})
```

