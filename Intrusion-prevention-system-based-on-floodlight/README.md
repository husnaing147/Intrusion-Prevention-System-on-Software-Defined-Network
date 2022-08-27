# Intrusion-prevention-system-based-on-floodlight
实现了snort和floodlight控制器的联动从而实现了基于floodlight的入侵防御系统

SDN的集中控制以及网络可编程的特性可以实现对网络的集中式保护，本项目通过将入侵检测工具snort和floodlight控制器上的防火墙模块联动实现了一种入侵防御系统，主要的思路是将snort部署到数据平面的OVS交换机上检测OVS交换机转发的流量，根据检测规则发现危险流量，并将警告消息通过socket通信发送给floodlight控制器，或者通过创建RESTful API将警告消息以JSON数据格式传递给floodlight控制器，floodlight控制器接收到警告事件后在防火墙模块上添加相应的过滤规则，从而阻止危险流量，实现入侵防御的功能。

注意：代码基于floodlight 1.2版本编写，需要自己下载floodlight 1.2然后将模块导入到floodlight工程当中，具体的步骤已发布到SDNLAB：https://www.sdnlab.com/20836.html