# MySQL group replication �ڵ���ӡ��ڵ�ɾ����MGR״̬��顢���ݿ���ͣ����
��������handle_mgr

### ����ṹ��
```
handle_mgr/
|-- bin/
|   |-- __init__.py
|   |-- handle_mgr.py
|
|-- core/
|   |-- __init__.py
|   |-- main.py  
|-- conf/
|   |-- mgr.conf   ##handle_mgr�����ļ�
|   |-- example_mgr.conf  ##�ο������ļ�
|-- README

```

### ���л�����
    Python3.0�����ϰ汾�������ɡ�


### ִ�з�����
    python3 handle_mgr.py
	
### ʹ�÷�����
    1) �༭�����ļ�conf/mgr.conf������Ϊ�����ļ���������:
	  ##[mgr]�������
	  [mgr]
	  ##����ΪMySQLʵ����½�û������롢socket��MySQL�����basedir��MySQLʵ��Ĭ�������ļ���
	  ##�û���Ҫ�����Լ�ʵ���������
      user = root    
      password = mysql   
      socket = /tmp/mysql3307.sock
      basedir = /usr/local/mysql57
      defaults-file = /57data/my.cnf
      
      ##����ΪMySQL group replication��صĲ�������
	  ##�û���Ҫ����ʵ��������ġ�
      transaction_write_set_extraction = XXHASH64     
      loose-group_replication_group_name = "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"
      loose-group_replication_start_on_boot = off
      loose-group_replication_local_address = "10.0.0.11:33071"
      loose-group_replication_group_seeds = "10.0.0.11:33071,10.0.0.13:33071,10.0.0.14:33071"
      loose-group_replication_bootstrap_group = off
      
	  ##����ΪMySQL group replication�ڲ�ͨѶ���û������룬
	  ##���û��ɱ����򴴽�������Ҫ��ǰ��������ӽڵ�ǰ�����ڸ��û��ᱨ��
      mgr_user = 'rpl_user'@'%'
      mgr_password = rpl_pass
	  
    2) ����ϵͳ��ʾ������Ҫ�Ĳ������͡�
	   1 : Check the MGR status
       2 : Add MGR member
       3 : Delete MGR member
       4 : Start MySQL instance
       5 : Stop MySQL instance
       6 : Start GROUP_REPLICATION
       7 : Stop GROUP_REPLICATION
       8 : Exit

