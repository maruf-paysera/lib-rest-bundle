# Change Log

## 5.1.2
### Added
- Added `Locked` when HTTP Lock status occur at `ApiException`

## 5.1.1
### Added
- Support for PHP >=7.4
- Support for Symfony 5.X
### Removed
- Support for Symfony 3.X

## 5.1.0
### Added
- Dockerfiles
- gitignore for `.phpunit.result.cache`
- Requirement for `doctrine/persistence` as there direct requirement in code at `RepositoryAwareEntityResolver`
- Test for `RepositoryAwareEntityResolver`
### Changed
- Readme
- `php:^7.1` => `php:^7.4`
### Removed
- `phpunit` setting that `phpunit` does not recognize
## 5.0.4
### Added
- Added support for PHP 8.0

## 5.0.3
### Fixed
- Fix deprecation notices for Symfony 4 - if method exists use `TreeBuilder->getRootNode()` instead of `TreeBuilder->root()`.

## 5.0.2
### Fixed
- `paysera_rest.normalizer.items_result` marked as `public`

## 5.0.1
### Added
- marked all services as `public`

## 5.0.0
### Changed
- `ApiManager` is now lazy-loaded and REST related request checking is moved to other services
### Removed
- Removed `ApiManager::addApiByUriPattern`, `ApiManager::addApiByKey` methods. Now compiler pass uses `RestApiRegistry::addApiByKey`,
`RestApiRegistry::addApiByUriPattern` methods for registering API's.
- Removed `ApiManager::getApiKeyForRequest`, now `RequestApiKeyResolver` is responsible for providing api keys.
- Removed `ApiManager::getApiForRequest`. Now `RequestApiResolver` is responsible for providing API's based on request.
- Removed `ApiManager::isRestRequest`, instead `RestListener` uses private `RestListener::isRestRequest` method.

## 4.4.1
### Fixed
Made service `paysera_rest.service.property_path_converter.camel_case_to_snake_case` public as it is being retrieved directly from the container.

## 4.4.0

### Changed
- Dropped support for PHP 5, Symfony 2
- Now requiring Symfony components individually, rather than requiring package `symfony/symfony`
- Updated PHPUnit and mockery/mockery
- Removed usage of use deprecated `Symfony\Component\Security\Core\Role\RoleHierarchyInterface`, now using `Symfony\Component\Security\Core\Role\RoleHierarchy`.

### Fixed
- Code style fixes

## 4.3.0
### Added
- `Paysera\Bundle\RestBundle\ApiManager::createErrorFromException()` - checks if exception contains status code *400* and creates `ApiException::InvalidRequest` error

## 4.2.2
### Fixed
- `Paysera\Bundle\RestBundle\Listener\RestListener::onKernelException()` increased listener priority to `10`. Since Symfony 3.3 the priority of `ExceptionListener::onKernelException` was changed to `1`.

## 4.2.1
### Changed
- `\Paysera\Bundle\RestBundle\RestApi::getValidationGroups()` no longer returns `null` if `\Paysera\Bundle\RestBundle\RestApi::$globalValidationGroups` is empty.

## 4.2.0
### Added
- New optional bundle configuration parameter `locales`

### Changed
- `\Symfony\Component\HttpFoundation\Request::getLocale` now can return preferred locale from the `Accept-Language` header, which resolves from the `locales` parameter in the bundle configuration

## 4.1.1
### Added
- Moved `Paysera\Bundle\RestBundle\Listener\RestListener::onKernelException` logging to service `Paysera\Bundle\RestBundle\Service\ExceptionLogger`

## 4.0.0
###  Changed
- `Paysera\Bundle\RestBundle\RestApi` property `propertyPathConverter` now has default value set to `CamelCaseToSnakeCaseConverter`

## 3.0.0
### Changed
- `Paysera\Bundle\RestBundle\Entity\Error` all properties are now private instead of protected
- `Paysera\Bundle\RestBundle\Exception\ApiException` all properties are private instead of protected
- `Paysera\Bundle\RestBundle\Exception\ApiException` 7th construct argument now is `violation` of type `Violation[]` instead of `codes` of type `string[]`
- 400 error response will no longer contain `errors` property instead if `error_properties_codes` property
### Removed
- `Paysera\Bundle\RestBundle\Entity\Error` removed `errorCodes` property and related getters/setters
- `Paysera\Bundle\RestBundle\Entity\Error` removed `toArray` method
- `Paysera\Bundle\RestBundle\Exception\ApiException` removed property getter and setter of `codes` property

## 2.1.0
### Changed
- `_format` route attribute is no longer used to detect Request or Response format.
`Content-Type` or `Accept` headers should be used accordingly.

## 2.0.3
### Deprecated
- Deprecated `_format` route attribute. In future releases request format will be always taken from `Content-Type` header.

## 2.0.0
### Changed
- Update factory service syntax
