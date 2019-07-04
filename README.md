# logger-audit-app
Insert log details in DB for future use and audit purpose.
This is the basic version and not followed mule standards.
User can modify according to their need.


You can use this app either copy-paste "common-logger-app.xml" which is having "common-logger-appFlow" flow along with DB global config.
OR
You can refer this project in other project as common utility.


#DB Create Table (DDL)
CREATE TABLE `logger` (
  `seqId` int(11) NOT NULL AUTO_INCREMENT,
  `correlationId` varchar(100) NOT NULL,
  `flowName` varchar(255) NOT NULL,
  `processorName` varchar(100) DEFAULT NULL,
  `payload` longtext,
  `loggedAt` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`seqId`)
) ENGINE=InnoDB AUTO_INCREMENT=22 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci


#How to refer in other projects
Steps-
	Export this app as mule-archive jar.
	Install this jar (local/server) using maven or anypoint install local file option.
	Update the pom and gives this app's dependency
		<dependency>
            <groupId>com.mycompany</groupId>
            <artifactId>common-logger-app</artifactId>
            <version>1.0.0-SNAPSHOT</version>
        </dependency>
	Import the mule config file from the app (file name : common-logger-app.xml)
	
Now you can use the flow (common-logger-appFlow) in your main application using flow reference.
Before calling this flow we will have to pass flowvar's (Check DB schema for optional vars) like vars.correlationId, vars.flowName,vars.processorName

Happy Learning
For any query/suggestion write me at hsingh904@gmail.com

