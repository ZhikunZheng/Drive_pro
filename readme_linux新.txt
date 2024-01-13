启动zookeeper：
bin/zookeeper-server-start.sh config/zookeeper.properties

启动kafka：
bin/kafka-server-start.sh config/server.properties

启动Mysql数据库：
nohup sudo systemctl start mysql

启动算法接口（每次重启算法时阈值会置为初始值）：
uvicorn Main:app --reload --port 8585 --host 0.0.0.0

启动SpringBoot接口：
java -jar dsj-0.0.1-SNAPSHOT.jar 

##正常只用从下面开始运行
跳转到目录下:
cd Drive_pro/

启动持续向kafka写数据：
python kafka_writing.py 

只有启动了向kafka写数据才能读到实时信息

调试接口：
关闭kafka读取数据接口：http://c416.ilisa.team:8844/rod/stop
筛选查询接口：http://c416.ilisa.team:8844/rod/select_query?rod_name=SA1.1&step=700
实时查询接口：http://c416.ilisa.team:8844/rod/time_query?rod_name=SA1.1
修改阈值接口：http://c416.ilisa.team:8844/rod/update?filename=LCTpickuptime&value=70-90  #修改吸合时间阈值
	     http://c416.ilisa.team:8844/rod/update?filename=LCresistance&value=1.6-1.9-2.3-2.6 #修改电阻阈值
查看阈值接口：http://c416.ilisa.team:8844/rod/list_rules?filename=LCTpickuptime	#查看吸合时间阈值
	     http://c416.ilisa.team:8844/rod/list_rules?filename=LCresistance  #查看电阻阈值

filename=
LCresistance    提升线圈电阻
MCresistance	移动线圈电阻
SCresistance	保持线圈电阻
LCTpickuptime	提升(o_mode = lift):提升线圈吸合时间
LCXpickuptime	下降(o_mode = ?):提升线圈吸合时间
MCTpickuptime	提升:移动线圈吸合时间
MCXpickuptime	下降:移动线圈吸合时间
SCTpickuptime	提升:保持线圈吸合时间
SCXpickuptime	下降:保持线圈吸合时间