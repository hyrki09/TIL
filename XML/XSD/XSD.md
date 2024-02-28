## XSD 개요

XSD는 XML 스키마 정의(XML Schema Definition)를 의미합니다.

XSD는 XML 문서의 구조 및 해당 문서가 포함할 수 있는 적법한 요소와 속성을 명시합니다.

즉, 해당 XML 문서가 유효한(valid) XML 문서로써 포함할 수 있는 관계를 정의합니다.

***

```
<?xml version="1.0" encoding="UTF-8" ?>

<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"

    targetNamespace="http://codingsam.com"

    xmlns="http://codingsam.com"

    elementFormDefault="qualified">

...

</xs:schema>
```
- xmlns:xs 속성은 XSD의 요소와 타입에 사용할 W3C의 XML 스키마 네임스페이스를 명시합니다.

- targetNamespace 속성은 요소를 정의할 XML 스키마 네임스페이스를 명시합니다.

- xmlns 속성은 기본 XML 스키마 네임스페이스를 명시합니다.

- elementFormDefault 속성은 해당 스키마를 이용해 선언한 XML 문서의 모든 요소가 네임스페이스를 만족한다는 것을 명시합니다.
