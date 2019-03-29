# Install Maya on CentOS



## Maya Version & CentOS Version

### [Maya 2018 & CentOS 7.6](docs/maya2018_centos7.6.md)

### [Maya 2017 & CentOS 7.6](docs/maya2017_centos7.6.md)


## 설치시 주의사항

### Product Key(제품키)

Client Computer에 마야 설치시 꼭 그버젼에 맞는 제품키를 인스톨러에 입력한다.
마야 2018를 설치하는데 `657H1`(마야 2016 제품키)를 입력하면 마야 실행시에 오류가 발생한다.

- Maya 2019: `657K1`
- Maya 2018: `657J1`
- Maya 2017: `657I1`
- Maya 2016: `657H1`

<참고> [2018: Autodesk 제품용 제품 키](https://knowledge.autodesk.com/ko/customer-service/download-install/activate/find-serial-number-product-key/product-key-look/2018-product-keys)

### Dependency(종속성)

Linux, 특히 Fedora 시스템의 경우, OS의 기정의 인스톨시에, Maya가 동작하기 위해 필요한 시스템 라이브러리의 일부가 인스톨 되지 않습니다. yum 를 사용하면, 추가가 필요한 시스템 의존 라이브러리를 검색해, 필요한 런타임 라이브러리를 구성할 수 있습니다.

