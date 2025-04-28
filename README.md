# Ouster-Driver-for-Apollo6.0  (support ARM and X86)  


1.   基于apollo6.0 的ouster lidar 驱动使用参考如下：

   1，解压附件后将ouster目录拷贝到apollo的“modules/drivers/lidar”目录下；

   2，修改”ouster/conf/ouster128.pb.txt“中的配置，“udp_dest_host”是工控机的IP，”hostname“为Lidar的IP。

   3, add ouster lidar to apollo/modules/drivers/lidar/BUILD:19 :
	`add "//modules/drivers/lidar/ouster:install", to this BUILD file`
	
      	....
	15	  deps = [
	16	"//modules/drivers/lidar/hesai:install",
	17	"//modules/drivers/lidar/robosense:install",
	18	"//modules/drivers/lidar/velodyne:install",
	19	"//modules/drivers/lidar/ouster:install",
		]
	....

   4，"apollo.sh build_opt_cpu drivers/lidar"编译成功后启动“cyber_launch start modules/drivers/lidar/ouster/launch/ouster128.launch”，然后通过cyber中查看相关的输出信息。

