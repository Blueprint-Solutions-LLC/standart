# API Стандартын Гарын авлага

Энэхүү баримт нь Blueprint Solutions компанийн бүх төсөлд мөрдөгдөх API бичих стандартуудыг тодорхойлно. Зорилго нь хөгжүүлэгчдэд нэгдсэн, ойлгомжтой, тогтвортой, өргөтгөгдөхүйц API бүтцийн жишгийг тогтоох юм.

---

## 1. Versioning

- Бүх API нь `/api/v1/...` хэлбэртэй version-тай байх
- Version нэмэгдэх нөхцөл:
  - Breaking changes
  - Authentication механизмыг бүхэлд нь өөрчлөх
  - Response format их хэмжээгээр өөрчлөгдөх
- Version route-д заавал тусгана:

✅ `/api/v1/users`  
❌ `/users`  

---

## 2. HTTP Method Стандарт

| Method  | Зориулалт                                      |
|---------|------------------------------------------------|
| GET     | Мэдээлэл авах (List, Detail)                   |
| POST    | Шинэ мэдээлэл үүсгэх                          |
| PUT     | Бүх мэдээллийг бүрэн шинэчлэх                 |
| PATCH   | Зөвхөн тодорхой хэсгийг өөрчлөх               |
| DELETE  | Мэдээллийг устгах                              |

Жишээ:
- GET    `/api/v1/users` → Хэрэглэгчдийн жагсаалт
- GET    `/api/v1/users/15` → Нэг хэрэглэгчийн мэдээлэл
- POST   `/api/v1/users` → Шинэ хэрэглэгч үүсгэх
- PUT    `/api/v1/users/15` → Хэрэглэгчийг бүхлээр нь шинэчлэх
- PATCH  `/api/v1/users/15` → Зөвхөн зарим талбарыг шинэчлэх
- DELETE `/api/v1/users/15` → Хэрэглэгчийг устгах

---

## 3. API Path Naming

- Нэр томьёо **plural** хэлбэрээр
- **kebab-case** биш, **snake_case** биш, зөвхөн **lowercase plural** ашиглана
- Action-тэй endpoint-д `/{resource}/{id}/action` хэлбэр ашиглана

✅ `/api/v1/products`  
✅ `/api/v1/users/5/verify`  
❌ `/api/v1/getUser`  
❌ `/api/v1/UserList`  

---

## 4. Query Parameters

GET `/api/v1/products?category_id=3&sort_by=price&order=asc&page=2&limit=10`

- Pagination → `page`, `limit`
- Filter → параметрээр дамжуулна
- Sort → `sort_by`, `order`

---

## 5. Response Format

Бүх response дараах бүтэцтэй байна:

```json
{
  "success": true,
  "message": "Амжилттай",
  "data": {
    "id": 15,
    "name": "Product Name"
  }
}
```

### Error Response:

```json
{
  "success": false,
  "message": "Мэдээлэл олдсонгүй",
  "errors": {
    "email": ["Хүчинтэй имэйл биш байна"]
  }
}
```

---

## 6. Resource Nesting

Харьяалагдсан өгөгдлүүдийг дараах байдлаар илэрхийлнэ:

- GET `/api/v1/companies/12/employees`
- GET `/api/v1/companies/12/employees/100`

---

## 7. Status Codes

| Code | Тайлбар                      |
|------|------------------------------|
| 200  | Амжилттай                    |
| 201  | Амжилттай үүссэн            |
| 204  | Амжилттай устсан, хоосон    |
| 400  | Bad request                  |
| 401  | Not authenticated            |
| 403  | Permission denied            |
| 404  | Not found                    |
| 422  | Validation error             |
| 500  | Server error                 |

---

## 8. Swagger (OpenAPI) Баримтжуулалт

- Бүх API-д OpenAPI 3.1 format-аар `docs/openapi.yaml` файл үүсгэнэ
- Swagger UI-г Dev environment-д байршуулж, автоматаар шинэчлэх боломжтой болгоно

Жишээ:
```yaml
paths:
  /api/v1/users:
    get:
      summary: Хэрэглэгчдийн жагсаалт
      responses:
        '200':
          description: Амжилттай
```

---

## 9. Хүснэгт бүрт log API заавал дагалдана

- POST `/api/v1/products/12/logs`
- GET  `/api/v1/products/12/logs`

---

## 10. URI Limit

- URI нь 200 тэмдэгтээс хэтрэхгүй байх
- Шаардлагатай тохиолдолд `POST` ашиглан JSON payload-р өгөгдөл дамжуулна
