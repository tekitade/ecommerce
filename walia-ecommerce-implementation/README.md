# Walia Ecommerce Implementation

## Introduction
Walia Ecommerce Implementation is a MuleSoft-based project designed to integrate various components of an ecommerce platform. This project focuses on streamlining data flows, enhancing connectivity, and ensuring seamless operations between different systems involved in the ecommerce ecosystem.

## Project Structure
The project is structured into the following main components:
- **API Layer**: Exposes RESTful APIs for various ecommerce functionalities.
- **Integration Layer**: Manages the flow of data between systems.
- **Data Transformation Layer**: Utilizes DataWeave for data mapping and transformation.
- **Error Handling Layer**: Ensures robust error handling and logging.

## Features
- **Product Management**: APIs for managing product catalog, including CRUD operations.
- **Order Management**: APIs for handling customer orders, including order creation, updates, and status tracking.
- **Customer Management**: APIs for managing customer data, including registration, updates, and retrieval.
- **Inventory Management**: Integration with inventory systems to manage stock levels and availability.
- **Payment Processing**: Integration with payment gateways for handling transactions securely.

## Prerequisites
- MuleSoft Anypoint Platform
- Anypoint Studio 7.x
- Java JDK 8,11 or 17
- Git

## Getting Started

### To secure the property file
java -cp secure-properties-tool.jar com.mulesoft.tools.SecurePropertiesTool file encrypt Blowfish CBC waliacoders local-unencrypted.yaml local.yaml

### Create a kafka topic
- For Windows:
```bash
 kafka-topics.bat --create --topic walia_ecommerce --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
 ```
- For Mac: 
```bash
./kafka-topics.sh --create --topic walia_ecommerce --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
 ```

### Deploy using Jenkins
I already add the cloud hub configuration in the pom.xml file so you don't need to add

```xml
<cloudHubDeployment>
						<uri>https://anypoint.mulesoft.com</uri>
						<muleVersion>${mule.version}</muleVersion>
						<username>${anypoint.username}</username>
						<password>${anypoint.password}</password>
						<applicationName>${appname}</applicationName>
						<businessGroup>${business}</businessGroup>
						<environment>${env}</environment>
						<workerType>${vCore}</workerType>
						<workers>${workers}</workers>
						<objectStoreV2>true</objectStoreV2>
					</cloudHubDeployment>
```

So in the maven deploy section run this command:

```bash
mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.3.0 -Danypoint.username=yourusername -Danypoint.password=yourpassword -Denv=Sandbox -Dappname=walia-ecommerce -Dbusiness=MuleSoft -DvCore=Micro -Dworkers=1 
```

### Clone the Repository
```bash
git clone https://github.com/MintesnotCraft/walia-ecommerce-implementation.git

