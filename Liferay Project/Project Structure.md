## Liferay Portal Services

- portal-kernel: provides interfaces and utils

- portal-impl: provides service implementations that implement those interfaces


## Liferay Module Services
- Service Builder: a model-driven code generation tool
  
      service.xml

- For Gradle Project, running the following command in module project’s root folder
 
      gradlew buildService
  
### *-api module: Service Builder generates classes and interfaces belonging to the **persistence layer**, **service layer**, and **model layer**
      
  - *Persistence: Persistence interface that defines **CRUD** methods for the entity such as create, read, update, and delete persistent objects
      
  - *Util: 
  
    - Persistence utility class that wraps *PersistenceImpl and provides direct access to the database for CRUD operations.
      
    - This utility should only be used by the service layer.
            
    - In your portlet classes, use *LocalServiceUtil or *ServiceUtil instead.
      
  - *LocalService: Local service interface.
      
  - *LocalServiceUtil: Local service utility class which wraps *LocalServiceImpl and serves as the primary local access point to the service layer.
      
  - *Service: Remote service interface.
      
  - *ServiceUtil: Remote service utility class which wraps *ServiceImpl and serves as the primary remote access point to the service layer.
      
  - *Model: Base model interface.
  
  - *: model interface which extends *Model
      
### *-service module: The implementation of the interfaces defined in the *-api module
      
  - *PersistenceImpl: Persistence implementation class that implements *Persistence.
      
  - *LocalServiceImpl: Local service implementation.
      
  - *ServiceImpl: Remote service implementation.
      
  - *Impl: Model implementation.
      
- Note:

  - *Util classes are generated for backwards compatibility purposes only. Module applications should avoid calling the util classes.

  - Shouldn't customize any of Persistence classes or interfaces.
      
  - Only three should be manually modified: *LocalServiceImpl, *ServiceImpl and *Impl.
      
  - Service Builder adds corresponding methods to the *LocalService, *Service and * interface the next time you run it.

## Reference

- https://help.liferay.com/hc/en-us/articles/360018160851-What-is-Service-Builder-
- https://help.liferay.com/hc/en-us/articles/360018160991-Finding-and-Invoking-Liferay-Services#finding-liferay-module-services
- https://help.liferay.com/hc/en-us/articles/360017881992-Running-Service-Builder-and-Understanding-the-Generated-Code
