# ListView瀑布流

```
contentContainerStyle={styles.listView}
listView:{
flexDirection:'row',
flexWrap:'wrap',
},

```
row可能需要设置确定的高度

如果出现renderRow执行的次数比dataSource的数量少的情况，  
需要设置:  
`initialListSize={20} // 可以把值改为dataSource的length`  
如果不设置,renderRow只能执行前几条数据, 想显示其他数据, 只能通过改变任意state来实现
