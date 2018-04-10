# Config Service

This project shows example of the oss config service.

The "@EnableConfigServer" annotation in the main class, enables this service to be a config server. It will read all the properties from the config repo, identified by `spring.cloud.config.server.git.uri` in `application.yml` file.

This example relies on following config repo `https://github.com/akoranne/configs`, specially `configserver.yml`.


## Local Build & Test
1. Build the project
	```
	$> ./mnvw clean package
	```

2. Run the project locally
	```
	$> ./mnvw spring-boot:run
	```

3. Test locally
	```
	Go to http://localhost:8888/configserver/default
	You should see the results
	```

## Cloud
1. Push to OSS CF or PCF
	```
	$> cf push
	```

2. Test locally
	```
	Go to - http://config-service.apps.<pcf-domain>/configserver/default
	You should see the jason document.
	```

**Note**: For PCF, use Spring Cloud Config Server from the market place. 


## Results

```
{  
   "name":"configserver",
   "profiles":[  
      "default"
   ],
   "label":null,
   "version":"a611374438e75aa1b9808908c57833480944e1a8",
   "state":null,
   "propertySources":[  
      {  
         "name":"https://github.com/spring-cloud-samples/config-repo/configserver.yml (document #0)",
         "source":{  
            "info.description":"configserver"
         }
      },
      {  
         "name":"https://github.com/spring-cloud-samples/config-repo/application.yml (document #0)",
         "source":{  
            "info.description":"Spring Cloud Samples",
            "info.url":"https://github.com/spring-cloud-samples",
            "eureka.client.serviceUrl.defaultZone":"http://localhost:8761/eureka/",
            "foo":"baz"
         }
      }
   ]
}
```
