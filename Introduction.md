# Design Purpose
  * Make entity definition and restful api configurable for backend service without changing the code or re-deploy
  * Make UI layouts and business logic configurable for frontend pages without changing the code or re-deploy
  * Increase product development efficiency
    * Provide visual editors for UI layouts and entity/api
    * Set strict rules and check automatically for frontend/backend configurations
    * Encapsulate components of larger granularity and fixed/limited features
  * Reduce chances of mistakes in development periods and deploy procedures
# Range of Application
  * All Comm100 software products can use autocoding framework to achieve their goal
  * We recommend all product modules and services use autocoding framework if they are following DDD methodology since autocoding framework also contains a set of DDD programming supports
  * For now, autocoding framework works better with the regular data model process business such as system configuration, entity CRUD, data presentation, unified page layout control, etc.
  * For particular business features such as 1to1 or group message transportation, 3rd party protocol adaptation and NLP, they require direct coding for the core implementations.
# DDD and ER-first Design Strategy
  * Autocoding framework follows the 4 layer model of domain driven design methodology
  * Generally every feature should first finish its ER design before implementation
  * When use autocoding, designed ER should be configured through autocoding framework, including entity definition, api definition, entity storage preparation, etc.
  * Entity will be used by both backend and frontend code
# Configurable Behavior
  * Some of the behaviors of API and UI components are also configurable such as
    * API data aggregations
    * Authentations methods
  * See the following documents for details