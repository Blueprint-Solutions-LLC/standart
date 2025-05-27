# API Standard Guide

Энэхүү repository нь Blueprint Solutions компанийн бүх төсөлд мөрдөгдөх API стандартын гарын авлага, жишээ, хэрэгжүүлэлтийн бүтцийг агуулна.

## Агуулга

- [API-ийн ерөнхий бүтэц](./api-guideline.md)
- [OpenAPI/Swagger бичиглэл](./docs/openapi.yaml)
- [Жишээ HTTP хүсэлтүүд](./examples)
- [Lint & Formatting тохиргоо](./.eslintrc.json, .prettierrc, .editorconfig, .husky)

## Зорилго

- Нэгдсэн API бүтэцтэй байх
- Бүх төсөлд хялбар интеграц хийх
- Хөгжүүлэгчдэд ойлгомжтой, тодорхой, шууд хэрэгжүүлэх боломжтой байх
- Тест болон баримтжуулалтад бүрэн бэлэн байх

## Ашиглах заавар

1. Төслийн root хавтсанд `docs/openapi.yaml`-г Swagger UI-тэй холбож ашиглана.
2. `examples` фолдер дахь `.http` файлуудыг VSCode REST Client ашиглан API-г туршиж болно.
3. Хөгжүүлэлтийн явцад `api-guideline.md` файлд заагдсан стандартуудыг дагана.

## Ашигласан технологи

- OpenAPI 3.1 (Swagger)
- ESLint
- Prettier
- Husky (pre-commit)
- EditorConfig