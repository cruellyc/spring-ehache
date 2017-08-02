# spring-ehache
1.添加 mybatis-ehcache.jar
<dependency>
			<groupId>org.mybatis</groupId>
			<artifactId>mybatis-ehcache</artifactId>
			<version>1.0.0</version>
		</dependency>
2.添加 mybatis-ehcache.jar 后可以直接在mapper.xml中加入以下代码：

<cache type="org.mybatis.caches.ehcache.EhcacheCache" >
		<property name="timeToIdleSeconds" value="3600"/>
		<property name="timeToLiveSeconds" value="3600"/>
		<property name="maxEntriesLocalHeap" value="1000"/>
		<property name="maxEntriesLocalDisk" value="10000000"/>
		<property name="memoryStoreEvictionPolicy" value="LRU"/>
	</cache>
  
##########当添加以上缓存功能是就不必添加以下的缓存配置，或添加以下缓存文档就不必添加以上的配置#############

1.添加相关jar
    <dependency>
			<groupId>net.sf.ehcache</groupId>
			<artifactId>ehcache</artifactId>
			<version>2.7.4</version>
		</dependency>
		<dependency>
			<groupId>net.sf.ehcache</groupId>
			<artifactId>ehcache-core</artifactId>
			<version>2.4.8</version>
		</dependency>
    
    2.添加配置文件 spring-ehcache.xml和 ehcache.xml
    3.在需要缓存的地方添加注解
         @Cacheable(value="userCache",key="#uid")//缓存
    4.在新增或修改删除时可添加注解清除缓存
      @CacheEvict(value="userCache",key="#uid",beforeInvocation=true)//清除缓存
    
