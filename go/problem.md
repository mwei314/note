# 踩坑记

## slice初始化问题
`make([]type, n)`这样初始化slice的时候，第二个参数是设置切片长度，不是容量，这样得到的是长度为n且元素为type零值的slice。  
如果想得到长度为0,容量为n的切片，用`make([]type, 0, n)`

## struct转json问题
struct中只有支持导出(首字母大写)的元素才能被JSON序列化