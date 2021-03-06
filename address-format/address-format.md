# Neuron 驱动地址格式

## 总则 {#endpoint-general}

本文档描述了 Neuron 与各种工业协议驱动程序之间的标签地址格式。每个 Neuron 驱动程序都有自己的地址格式，在配置过程中会被解析，用于机器或设备的通信。

## Allen-Bradley PLC2（半双工） {#endpoint-PLC2}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_df1hp2 |
| 驱动名称       | df1hp2          |
| 协议           | DF1（半双工）   |
| 物理接口       | RS485           |
| 默认设置       | 9600/8/N/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!DST!ADDR</span>

**STN** 为从站设备号

**DST** 为目的节点（CPU）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  |     | DDDDD | 0 ~ 65535 | 寄存器（字） |

注：由于 1771KG 是直接与 CPU 连接的，所以 STN 和 DST 应设置为同一编号（1771KG 模块的地址）。

例如：16! 16 (从属号码 20 八进制)

**16！16！520**（字 1010 八进制中的从数 20 八进制）。

在 KG 模式下，1771-KG 设置为 8（10 八进制），1785-KE 和 1770-KF2 设置为 0。

## Allen-Bradley PLC5（半双工） {#endpoint-PLC5}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_df1ph5 |
| 驱动名称       | df1ph5          |
| 协议           | DF1（半双工）   |
| 物理接口       | RS485           |
| 默认设置       | 9600/8/N/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!DST!ADDR</span>

**STN** 为从站设备号（KE/KF2 模块地址）

**DST** 为目的节点（CPU）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  |     | DDDDD | 0 ~ 65535 | 寄存器（字） |

注：KE 或 KF2 模块插入它的地址作为源，这个地址将是 PLC5 中使用的数据文件号。

例如：28！16（ KE/KF2 模块号 34 八进制，目的节点 = CPU 号 20 八进制）。

**28！16！10** 表示文件 N28 中的字 10 在从机号 20（八进制）。

在 KG 模式下，1771-KG 设置为 8（10 八进制），1785-KE 和 1770-KF2 设置为 0。

## Schneider TSX7 SCM (Modbus RTU) {#endpoint-TSX7-SCM}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_tsxmbr |
| 驱动名称       | tsxmbr          |
| 协议           | Modbus RTU      |
| 物理接口       | RS232           |
| 默认设置       | 9600/8/N/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为从站设备号（CPU）（1 – 247）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  | W   | DDDDD | 0 ~ 32767 | 寄存器（字） |

例如：**10！W100** 表示从站 10 中的字 100。

## Schneider TSX7 SCM (Modbus TCP) {#endpoint-TCP}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_tsxmbt |
| 驱动名称       | tsxmbt          |
| 协议           | Modbus TCP      |
| 物理接口       | 以太网          |
| 默认设置       | 端口：502       |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 是指如下的寄存器地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  | W   | DDDDD | 0 ~ 32767 | 寄存器 |

例如：**W4000** 表示字地址 4000。

## Schneider Telemecanique UNI-TE {#endpoint-UNI-TE}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_unite                                                                     |
| 驱动名称       | unite                                                                              |
| 协议           | TSX SCM 2161（Uni-Telway），直接在 V4（或更高版本） CPU 上的内置 UNI-TE 端口上使用 |
| 物理接口       | RS232                                                                              |
| 默认设置       | 9600/8/N/1                                                                         |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为从站设备号（Ad0 in CPU）（1 – 31）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  | W   | DDDDD | 0 ~ 32767 | 寄存器（字） |

例如：**1！W100** 表示从站 1 中的字 100。

## ABB SattControl Comli {#endpoint-Comli}

### 一般资讯

| 設定			 | 参数		      |
| -------------- | -------------- |
| 运行时模块     | neuron_o_comli |
| 驱动名称       | comli          |
| 协议           | COMLI          |
| 物理接口       | RS232          |
| 默认设置       | 9600/8/N/1     |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为从站设备号（CPU）（1 – 247）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  | W   | DDDDD | 0 ~ 3071 | 寄存器（字） |

例如：**1！R100** 表示从站 1 中的字 100。

## Omron Single HostLink (点对点) {#endpoint-Single-HostLink}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_omrhls           |
| 驱动名称       | omrhls                    |
| 协议           | Host-Link sysmac c-series |
| 物理接口       | RS232                     |
| 默认设置       | 9600/8/N/1                |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  | AR  | DDDDD | 0 ~ 4095  | 辅助继电器       |
| 字  | IR  | DDDDD | 0 ~ 4095  | I/O 和内部继电器 |
| 字  | HR  | DDDDD | 0 ~ 4095  | 保持中继         |
| 字  | LR  | DDDDD | 0 ~ 4095  | 链接中继         |
| 字  | TC  | DDDDD | 0 ~ 255   | 定时器           |
| 字  | DM  | DDDDD | 0 ~ 9999  | 数据寄存器       |

例如：**DM100** 表示 DM 数据存储区的字 100。

## Omron Multiple HostLink (主从模式) {#endpoint-HostLink}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_omrhls           |
| 驱动名称       | omrhls                    |
| 协议           | Host-Link sysmac c-series |
| 物理接口       | RS232                     |
| 默认设置       | 9600/8/N/1                |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为站号/模块号（0-31）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍     | 描述         |
| --- | --- | ----- | -------- | ------------ |
| 字  | AR  | DDDDD | 0 ~ 4095 | 辅助继电器       |
| 字  | IR  | DDDDD | 0 ~ 4095 | I/O 和内部继电器 |
| 字  | HR  | DDDDD | 0 ~ 4095 | 保持中继         |
| 字  | LR  | DDDDD | 0 ~ 4095 | 链接中继         |
| 字  | TC  | DDDDD | 0 ~ 255  | 定时器           |
| 字  | DM  | DDDDD | 0 ~ 9999 | 数据寄存器       |

例如：**10！DM100** 表示从机 10 的数据存储器中的字 100。

## Siemens S5 3964R/RK512 {#endpoint-siemens-s5}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_s539rk |
| 驱动名称       | s539rk          |
| 协议           | 3964R/RK512     |
| 物理接口       | RS232           |
| 默认设置       | 9600/8/N/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 为以下地址

DB 是数据块（0 - 999）

DBW（**字偏移量**）是该数据块中的数据字

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字  | I           | DDDD        | 0 ~ 4095            | 输入       |
| 字  | Q           | DDDD        | 0 ~ 4095            | 输出       |
| 字  | M           | DDDD        | 0 ~ 4095            | 标记存储器 |
| 字  | DB0~999.DBW | DDDDD<br>DDDDD | 0 ~ 65535<br>0 ~ 65535 | 数据存储器 |
| 字  | T           | DDD         | 0 ~ 255             | 定时器     |
| 字  | C           | DDD         | 0 ~ 255             | 计数器     |

例如：DB100（数据块 100）

**DB100.DBW20** (DBddd.DBWddddd) 指数据块 100 中的数据字 20

## Siemens S7 3964R/RK512 {#endpoint-siemens-s7}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_s739rk |
| 驱动名称       | S739rk          |
| 协议           | 3964R/RK512     |
| 物理接口       | RS232           |
| 默认设置       | 9600/8/N/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 为以下地址

DB 是数据块（0 - 999）

DBW（**字偏移量**）是该数据块中的数据字

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字节 | I           | DDDD        | 0 ~ 4095            | 输入                               |
| 字节 | Q           | DDDD        | 0 ~ 4095            | 输出                               |
| 字节 | M           | DDDD        | 0 ~ 4095            | 标记存储器                         |
| 字节 | DB0~999.DBW | DDDDD<br>DDDDD | 0 ~ 65535<br>0 ~ 65535 | 数据存储器（必须是偶数字节号）字节 |
| 字节 | T           | DDD         | 0 ~ 255             | 定时器                             |
| 字节 | C           | DDD         | 0 ~ 255             | 计数器                             |

注意：应使用真实的 DBW（如 DBW0、DBW2 等），驱动程序将从 0 开始读取字节，从 2 开始读取字节，它分别从字节 0、字节 2 读取一个字。

例如：DB100（数据块 100）

**DB100.DBW20** (DBddd.DBWddddd) 指数据块 100 中的数据字 20

## Siemens FETCH/WRITE {#endpoint-siemens-fetch}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_siefw               |
| 驱动名称       | siefw                        |
| 协议           | Siemens Fetch/Write Protocol |
| 物理接口       | 以太网                       |
| 默认设置       | 端口：2200                   |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 为以下地址

DB 是数据块（0 - 999）

DBW（**字偏移量**）是该数据块中的数据字（起始）

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字节 | IW           | DDDD        | 0 ~ 4095            | 输入                               |
| 字节 | QW           | DDDD        | 0 ~ 4095            | 输出                               |
| 字节 | MW           | DDDD        | 0 ~ 4095            | 标记存储器                         |
| 字节 | DB0~999.DBW | DDDDD<br>DDDDD | 0 ~ 65535<br>0 ~ 65535 | 数据存储器（必须是偶数字节号）字节 |
| 字节 | T            | DDD         | 0 ~ 255             | 定时器                             |
| 字节 | C            | DDD         | 0 ~ 255             | 计数器                             |

注意：协议中有一个限制。DB 只能在 1-255 之间，读写表的起始地址不能超过 DBW2047，然而表的末端可以。但在测试过程中，可以从地址 DBW32766 开始。

注意：在 Simatic PLC 中，您只需定义一个 TCP/IP 连接，用于 FETCH 被动（只读）或 WRITE 被动（只写），在某个端口上监听。目前没有 FETCH/WRITE 被动设置，所以需要两个不同端口的连接，一个用于读，一个用于写。

例如：**DB100.DBW20** (DBddd.DBWddddd) 指数据块 200 中的数据字 20

## Siemens 工业以太网 S7 ISOTCP {#endpoint-siemens-industrial}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_s7pro        |
| 驱动名称       | s7pro                 |
| 协议           | S7 ISO TCP（S7 协议） |
| 物理接口       | 以太网                |
| 默认设置       | 端口：102             |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 为以下地址

注意：DB 是数据块（0 - 999）

DBW（**字偏移量**）是该数据块中的数据字（起始）

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 字节 | IW           | DDDD        | 0 ~ 4095            | 输入                               |
| 字节 | QW           | DDDD        | 0 ~ 4095            | 输出                               |
| 字节 | MW           | DDDD        | 0 ~ 4095            | 标记存储器                         |
| 字节 | DB0~999.DBW | DDDDD<br>DDDDD | 0 ~ 65535<br>0 ~ 65535 | 数据存储器（必须是偶数字节号）字节 |
| 字节 | T            | DDD         | 0 ~ 255             | 定时器                             |
| 字节 | C            | DDD         | 0 ~ 255             | 计数器                             |

例如：**DB100.DBW20** (DBddd.DBWddddd) 指数据块 200 中的数据字 20。

S7P_SCRTSAP 是 S7 协议的源 TSAP

S7P_DSTTSAP 是 S7 协议的目标 TSAP

## Mitsubishi FX0S/FX0N/FX1S/FX1N/FX2 {#endpoint-mitsubishi-fx0s}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_fxnpro |
| 驱动名称   | fxnpro          |
| 协议       | RS 命令         |
| 物理接口   | RS232           |
| 默认设置   | 9600/7/E/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 是<u>寄存器</u>地址

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 比特  | X   | OOO  | 0 ~ 377     | 输入继电器          |
| 比特  | Y   | OOO  | 0 ~ 377     | 输出继电器          |
| 比特  | M   | DDDD | 0 ~ 7999    | 辅助继电器          |
| 比特  | T   | DDD  | 0 ~ 255     | 计时器继电器        |
| 比特  | C   | DDD  | 0 ~ 255     | 计数器继电器        |
| 比特  | SM  | DDDD | 8000 ~ 9999 | 特殊辅助设备 继电器 |
| 比特  | S   | DDDD | 0 ~ 4095    | 国家                |
| 字    | TN  | DDD  | 0 ~ 255     | 定时器存储器        |
| 字    | CN  | DDD  | 0 ~ 199     | 计数器存储器        |
| 字    | D   | DDDD | 0 ~ 7999    | 数据寄存器          |
| 双字  | CN2 | DDD  | 200 ~ 255   | 计数器存储器        |
| 字    | SD  | DDDD | 8000 ~ 9999 | 特殊数据寄存器      |

例如：**D100** 表示在 D 数据存储区的字 100。

## Mitsubishi FX2N/FX3U/FX3G 系列 {#endpoint-mitsubishi-fx2n}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_fx3u3g |
| 驱动名称   | fx3u3g          |
| 协议       | RS 命令         |
| 物理接口   | RS232           |
| 默认设置   | 9600/7/E/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 是如下<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 比特  | X   | OOO  | 0 ~ 377     | 输入继电器          |
| 比特  | Y   | OOO  | 0 ~ 377     | 输出继电器          |
| 比特  | M   | DDDD | 0 ~ 7999    | 辅助继电器          |
| 比特  | T   | DDD  | 0 ~ 255     | 计时器继电器        |
| 比特  | C   | DDD  | 0 ~ 255     | 计数器继电器        |
| 比特  | SM  | DDDD | 8000 ~ 9999 | 特殊辅助设备 继电器 |
| 比特  | S   | DDDD | 0 ~ 4095    | 国家                |
| 字    | TN  | DDD  | 0 ~ 255     | 定时器存储器        |
| 字    | CN  | DDD  | 0 ~ 199     | 计数器存储器        |
| 字    | D   | DDDD | 0 ~ 7999    | 数据寄存器          |
| 双字  | CN2 | DDD  | 200 ~ 255   | 计数器存储器        |
| 字    | SD  | DDDD | 8000 ~ 9999 | 特殊数据寄存器      |
| 字    | R   | DDDD | 0 ~ 32767   | 扩展寄存器          |

例如：**D100** 表示在 D 数据存储区的字 100。

## Mitsubishi Melsec E71 for Q 系列 {#endpoint-mitsubishi-melsec}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块     | neuron_o_mele71 |
| 驱动名称       | mele71          |
| 协议           | MELSEC E71      |
| 物理接口       | 以太网          |
| 默认设置       | 端口：2000      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">ADDR</span>

**ADDR** 是如下<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 比特 | X   | HHHH    | 0 ~ 1fff    | 输入继电器                   |
| 比特 | Y   | HHHH    | 0 ~ 1fff    | 输出继电器                   |
| 比特 | M   | DDDDD   | 0 ~ 61439   | 内部继电器                   |
| 比特 | L   | DDDDD   | 0 ~ 32767   | 锁定继电器                   |
| 比特 | F   | DDDDD   | 0 ~ 32767   | <u>报幕员</u>                |
| 比特 | V   | DDDDD   | 0 ~ 32767   | 边缘继电器                   |
| 比特 | B   | HHHH    | 0 ~ efff    | 链接中继                     |
| 比特 | TC  | DDDD    | 0 ~ 2047    | 定时器线圈                   |
| 比特 | SS  | DDDDD   | 0 ~ 25471   | 保留计时器触点               |
| 比特 | SC  | DDDDD   | 0 ~ 25471   | 固定式定时器线圈             |
| 比特 | CS  | DDDDD   | 0 ~ 25471   | <u>Counter Contact</u>       |
| 比特 | CC  | DDDDD   | 0 ~ 25471   | 计数器线圈                   |
| 比特 | SB  | HHH     | 0 ~ 7ff     | 特殊链路继电器               |
| 比特 | DX  | HHHH    | 0 ~ 1fff    | 直接输入                     |
| 比特 | DY  | HHHH    | 0 ~ 1fff    | 直接输出                     |
| 比特 | TS  | DDDD    | 0 ~ 2047    | 定时器触点                   |
| 字   | W   | HHHH    | 0 ~ 2fff    | <u>Link Register</u>         |
| 字   | TN  | DDDD    | 0 ~ 2047    | 定时器当前值                 |
| 字   | SN  | DDDD    | 0 ~ 2047    | 保留计时器电流               |
| 字   | CN  | DDDD    | 0 ~ 1023    | 计数值                       |
| 字   | SW  | HHH     | 0 ~ 7ff     | <u>Special Link Register</u> |
| 字   | Z   | DD      | 0 ~ 19      | 索引寄存器                   |
| 字   | ZR  | HHHHH   | 0 ~ fe7a5   | <u>File Register</u>         |
| 字   | D   | DDDDDDD | 0 ~ 4212735 | 数据寄存器                   |
| 字   | SD  | DDDD    | 0 ~ 2047    | <div></div>                  |

例如：**D100** 表示在 D 数据存储区的字 100。

## Modbus RTU {#endpoint-modbus-rtu}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_mbsrtu |
| 驱动名称   | mbsrtu          |
| 协议       | Modbus RTU      |
| 物理接口   | RS485           |
| 默认设置   | 9600/8/N/1      |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为从机号或设备 ID（0-247）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 比特 | 01/05/15 | DDDDDD | 000001 ~ 065536 | 离散输出线圈       |
| 比特 | 02       | DDDDDD | 100001 ~ 165536 | 离散输入触点       |
| 字   | 04       | DDDDDD | 300001 ~ 365536 | 模拟输入寄存器     |
| 字   | 03/06/16 | DDDDDD | 400001 ~ 465536 | 模拟输出保持寄存器 |

## Modbus TCP {#endpoint-modbus-tcp}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_mbstcp |
| 驱动名称   | mbstcp          |
| 协议       | Modbus TCP      |
| 物理接口   | 以太网          |
| 默认设置   | 端口：502       |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为从机号或设备 ID（0-247）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 比特 | 01/05/15 | DDDDDD | 000001 ~ 065536 | 离散输出线圈       |
| 比特 | 02       | DDDDDD | 100001 ~ 165536 | 离散输入触点       |
| 字   | 04       | DDDDDD | 300001 ~ 365536 | 模拟输入寄存器     |
| 字   | 03/06/16 | DDDDDD | 400001 ~ 465536 | 模拟输出保持寄存器 |

例如：**2！404001** 表示字地址 4000，在子号 2 中。

## Modbus RTU over TCP {#endpoint-modbus-rtu-tcp}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_mbstcp |
| 驱动名称   | mbstcp          |
| 协议       | Modbus TCP      |
| 物理接口   | 以太网          |
| 默认设置   | 端口：502       |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">STN!ADDR</span>

**STN** 为从机号或设备 ID（0-247）

**ADDR** 是指如下的<u>寄存器</u>地址：

| 类  |     | 規格  | 範圍      | 描述         |
| --- | --- | ----- | --------- | ------------ |
| 比特 | 01/05/15 | DDDDDD | 000001 ~ 065536 | 离散输出线圈       |
| 比特 | 02       | DDDDDD | 100001 ~ 165536 | 离散输入触点       |
| 字   | 04       | DDDDDD | 300001 ~ 365536 | 模拟输入寄存器     |
| 字   | 03/06/16 | DDDDDD | 400001 ~ 465536 | 模拟输出保持寄存器 |

例如：**2！404001** 表示字地址 4000，在子号 2 中。

## IEC 61850 {#endpoint-iec-61850}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_i61850 |
| 驱动名称   | i61850          |
| 协议       | IEC 61850       |
| 物理接口   | 以太网          |
| 默认设置   | 端口：102       |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">FC!ADDR</span>

**FC** 是功能约束值，如下所示：

| 类  |   規格       | 描述         |
| --- | -----  | ------------ |
| 0   | IEC61850_FC_ST | 状态信息          |
| --- | -------------- | ----------------- |
| 1   | IEC61850_FC_MX | 测量值 - 模拟值   |
| 2   | IEC61850_FC_SP | 设定点            |
| 3   | IEC61850_FC_SV | 替换              |
| 4   | IEC61850_FC_CF | 配置              |
| 5   | IEC61850_FC_DC | 说明              |
| 6   | IEC61850_FC_SG | 设置组            |
| 7   | IEC61850_FC_SE | 设置组别可编辑    |
| 8   | IEC61850_FC_SR | 服务响应/服务跟踪 |
| 9   | IEC61850_FC_OR | 操作收到          |
| 10  | IEC61850_FC_BL | 屏蔽              |
| 11  | IEC61850_FC_EX | 扩展定义          |
| 12  | IEC61850_FC_CO | 控制              |
| 13  | IEC61850_FC_US | 单播 SV           |
| 14  | IEC61850_FC_MS | 多播 SV           |
| 15  | IEC61850_FC_RP | 无缓冲报告        |
| 16  | IEC61850_FC_BR | 缓冲报告          |
| 17  | IEC61850_FC_LG | 日志控制块        |

**ADDR** 是对象参考地址字符串

EC61850 数据分层模型通常有以下几种：

物理设备（IED）

逻辑设备（LD）

逻辑节点（LN）

对象数据（DO）

对象属性（DA）

例如：**1!testmodelSENSORS/TTMP1.TmpSv.instMag.f** 表示该标签的功能约束为 1（IEC61850_FC_MX--模拟测量器）。对象参考地址串为 (IED)--测试模型，(LD)--传感器，(LN)--TTMP1，(DO)--TmpSv，(DA)--instMag.f 为浮动值。

## OPC UA {#endpoint-opc-ua}

### 一般资讯

| 設定			 | 参数			   |
| -------------- | --------------- |
| 运行时模块 | neuron_o_opcua |
| 驱动名称   | opcua          |
| 协议       | OPC UA         |
| 物理接口   | 以太网         |
| 默认设置   | 端口：4840     |

### 地址格式
> <span style="font-family:sans-serif; font-size:2em;">IX!NODEID</span>

**IX** 为命名空间索引（1-32767）

**NODEID** 是节点 ID（任意字符串，不包括 '!'）

例如：2!Device1.Module1.Tag1 代表命名空间索引为 2，节点 ID 为 Device1.Module1.Tag1

命名空间索引和节点 ID 的解释请参考 OPC UA 标准。
