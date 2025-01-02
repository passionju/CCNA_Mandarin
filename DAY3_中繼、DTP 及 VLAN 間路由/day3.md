# 第三天 中繼、DTP 及 VLAN 間路由
##  配置並驗中繼鏈路
>中繼是一個可以承載多種流量類型，  
每種流量類型都用一個獨特的 VLAN ID 做了標記，的交換機連接埠。
這樣做後接收的Switch就能分辨哪個數據是哪個vlan  


### 將需要的接口配置變一個二層交換端口
`switchport`指令去切換變二層   
(註:此指令只在相容三層或多層交換器上需要。二層交換器上並不適用。  
那些支援指令`ip routing` 的交換器才被認為是與三層相容的交換器。)

這是透過執行 `switchport trunk encapsulation [option]` 指令完成的。選擇中繼連結所要使用的封裝協定。  
+ [dot1q] 強制該交換機端口使用 IEEE 802.1Q 封裝方式。  
+ [isl] 強制該交換機端口使用思科 ISL 封裝方式。  
+ [negotiate] 關鍵字則指明說在動態交換機間鏈路協議（Dynamic Inter-Switch Link Protocol, DISL）  
及動態中繼協議（Dynamic Trunking Protocol, DTP）封裝格式無法達成一致時，**ISL 作為備選格式**。

### DISL:  
DISL 簡化了兩台互聯的快速以太網設備間 ISL 中繼鏈路的建立  
。在 DISL 協議下，只需鏈路的一端需要配置為中繼端口，因此而將 VLAN 中繼配置過程大大簡化。  

### DTP:  
cisco專有的點對點協議P2P,它在兩台交換器間協商建立起某種常見中繼模式。

### 查看端口配置`show interfaces [name] switchport`
![alt text](image.png)

