# raspberrypi-digital-1637--x-temp-time-and-so-
使用tm1637数码管，显示温度，温度，时间等信息。

1,tm1637，3642BS，4个引脚:
  CLK, DIO, GND, VCC
  
2C数据格式如下：
    无数据：SCL=1，SDA=1；
    开始位（Start）：SCL=1，SDA由1向0跳变；
    停止位（Stop）：SCL=1，SDA由0向1跳变；
    数据位：当SCL由0向1跳变时，由发送方控制SDA，此时SDA为有效数据，不可随意改变SDA；
    当SCL保持为0时，SDA上的数据可改变；
    地址位：定义同数据位，但只由Master发给Slave；
    应答位（ACK）：当发送方传送完8位时，发送方释放SDA，由接收方控制SDA，且SDA=0；
    否应答位（NACK）：当发送方传送完8位时，发送方释放SDA，由接收方控制SDA，且SDA=1。
    当数据为单字节传送时，格式为：
    开始位，8位地址位（含1位读写位），应答，8位数据，应答，停止位。
    当数据为一串字节传送时，格式为：
    开始位，8位地址位（含1位读写位），应答，8位数据，应答，8位数据，应答，……，8位数据，应答，停止位。


操作细节如下：
    可在tm1637.py中看到细节。
                                                                    