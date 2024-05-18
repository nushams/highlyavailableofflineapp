# Multi-Tenant Point-of-Sale Software

## Overview
This project involves developing a multi-tenant point-of-sale (POS) software solution tailored for rental businesses. The software allows tenants to manage their rental operations, including renting equipment/tools to customers. The solution is designed to function as a web-based SaaS application hosted on the cloud, utilizing a relational SQL database.

## Key Features
- **Rental Management**: Rent out available equipment/tools to customers for a specified period.
- **Web SaaS on Cloud**: Accessible via the web and hosted on the cloud.
- **Offline Functionality**: Supports offline operations and synchronizes with the cloud when back online.

## Solution Description
![image](https://github.com/nushams/highlyavailableofflineapp/assets/109551022/542014bb-f739-41fe-a01e-3f3845155021)

### Architecture Components

1. **Web and Mobile Applications**: 
   - **Offline Access and Synchronization**: Both web and mobile apps support offline functionality and synchronize with the cloud when reconnected.

2. **Authentication and Identity Management**:
   - **Microsoft Entra ID**: Used as the primary identity provider. Other providers (e.g., Google, Facebook) can also be integrated.

3. **Routing and Load Balancing**:
   - **Azure Front Door**: Handles initial requests, load balancing, SSL termination, failover, and security (via Web Application Firewall).
   - **Azure DNS**: Manages DNS records and routes to the correct Azure Front Door endpoint.
   - **Application Gateway**: Routes and load-balances traffic to the appropriate Azure App Service.

4. **Web Hosting and APIs**:
   - **Azure App Service**: Hosts the web and mobile applications, offering automatic scaling and DevOps integration for continuous deployment.

5. **Data Management**:
   - **Azure SQL Elastic Pools**: Manages relational data, optimizing resource allocation and ensuring scalability and security. Each tenant gets a dedicated database within a pool.
   - **Azure Cache for Redis**: Provides in-memory caching to enhance performance and reduce latency.
   - **Azure AI Search**: Implements advanced search functionality within the applications.

6. **Offline Sync**:
   - **Azure Mobile App SDKs**: Facilitate offline data sync, ensuring applications remain functional during network outages.

7. **Storage and Security**:
   - **Azure Storage**: Utilizes Blob storage with geo-redundancy for durability and availability of data.
   - **Azure Key Vault**: Stores sensitive information securely.

8. **Monitoring and Error Handling**:
   - **Azure Monitor and Application Insights**: Provide comprehensive monitoring and error handling capabilities.
   - **Health Checks**: Regular health checks ensure system reliability.

9. **Continuous Integration and Deployment**:
   - **Azure DevOps**: Manages CI/CD pipelines for updates and deployments.
   - **GitHub Actions**: Alternative tool for CI/CD.

### Primary Components

- **Azure Front Door**: Regional load balancer that routes client traffic to the correct region, offering failover and security.
- **Microsoft Entra ID**: Identity provider for authentication and authorization.
- **Azure DNS**: Resolves domain names for multi-tenant access.
- **Application Gateway**: Internal traffic routing and load balancing.
- **App Service**: Preferred service for HTTP-based applications, web content, APIs, and business logic.
- **Azure SQL Elastic Pools**: Manages databases efficiently, providing resources on demand.
- **Azure AI Search**: Enhances search functionality with AI capabilities.
- **Azure Cache for Redis**: Provides caching to improve performance.
- **Offline Sync**: Ensures application usability during connectivity issues.
- **Azure Storage**: Cloud storage for data redundancy and durability.
- **Azure Key Vault**: Secure storage for sensitive information.
- **Azure Monitor**: Offers application and infrastructure observability.

### Alternative Components

- **Azure SQL Server**: Dedicated instances for tenants requiring more control over their databases.
- **Azure Traffic Manager**: Alternative for traffic distribution across datacenters.

## Notes
- **Resource Calculation**: An estimated calculation of Azure resources required is provided in a separate file.
