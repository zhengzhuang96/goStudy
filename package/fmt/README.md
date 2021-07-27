## package fmt

fmt包实现了类似C语言prinf和scan的格式化I/O。格式化动作（'verb'）源自C语言但更简单

#### verb:

通用：
```go
%v    值的默认格式表示
%+v   类似%v，但输出结构体时会添加字段名
%#v   值的go语法表示
%T    值的类型的Go语法表示
%%    百分号
```

布尔值：
```go
%T    单词true或false
```

整数：
```go
%b    表示为二进制
%c    改值对应的unicode码值
%d    表示为十进制
%o    表示为八进制
%q    该值对应的单引号括起来的go语法字符字面值，必要时会采用安全的转义表示
%x    表示为十六进制，使用a-f
%X    表示为十六进制，使用A-F
%U    表示为Unicode格式：U+1234，等价于"U+%04X"
```

浮点数与负数的两个组分：
```go
%b    无小数部分、二进制指数的科学计数法，如-123456p-78
%e    科学计数法，如-1234.456e+78
%E    科学计数法，如-1234.456E+78
%f	  有小数部分但无指数部分，如123.456
%F	  等价于%f
%g	  根据实际情况采用%e或%f格式（以获得更简洁、准确的输出）
%G	  根据实际情况采用%E或%F格式（以获得更简洁、准确的输出）
```

字符串和[]byte：
```go
%s	  直接输出字符串或者[]byte
%q	  该值对应的双引号括起来的go语法字符串字面值，必要时会采用安全的转义表示
%x	  每个字节用两字符十六进制数表示（使用a-f）
%X	  每个字节用两字符十六进制数表示（使用A-F）
```

指针：
```go
%p	表示为十六进制，并加上前导的0x
```

宽度通过一个紧跟在百分号后面的十进制数指定，如果未指定宽度，则表示值时除必需之外不作填充。精度通过（可选的）宽度后跟点号后跟的十进制数指定。如果未指定精度，会使用默认精度；如果点号后没有跟数字，表示精度为0。举例如下：
```go
%f:    默认宽度，默认精度
%9f    宽度9，默认精度
%.2f   默认宽度，精度2
%9.2f  宽度9，精度2
%9.f   宽度9，精度0
```