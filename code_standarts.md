# Blueprint Solutions LLC

## Кодын стандарт

### 1. Ойлгогдохуйц:
- Хувьсагч, функц, обьект болон файлуудын нэрийг өгөхдөө утга учиртай, тодорхой илэрхийлэл ашиглах.
- Тогтмол нэршлийн дүрмийг мөрдөх:  
  - Хувьсагч: `camelCase`
  - Функц: `snake_case`
  - Обьект: `PascalCase`

### 2. Коммент болон тайлбар:
- Комментыг бичихдээ юу хийдэг болон яагаад хэрэгтэйг тайлбарлах.
- Бүх обьект болон функцуудад толгой оруулах:
  ```javascript
  /** 
   * Fetches user details by ID from the API. 
   * 
   * Author: John Doe 
   * Date: January 16, 2025 
   * 
   * @param {string} userId - The ID of the user to fetch. 
   * @returns {Observable<User>} - An Observable containing the user details. 
   * @throws {Error} - Throws an error if the request fails. 
   */
  ```

### 3. Алдааг тодорхойлох:
- Алдаа гарах нөхцөлүүдийг тодорхойлж, барьж авах.

### 4. Editor-ийн тохиргоо:
- **Indentation**: 2 зай.
- **Line ending**: Line Feed (LF).
- **Charset**: UTF-8.

## API Стандарт

### 1. RESTful Practices:
- `GET` for retrieval.
- `POST` for creation.
- `PUT`/`PATCH` for updates.
- `DELETE` for deletions.
- Утга учиртай статус код ашиглах (200, 201, 404, 500).

### 2. Endpoint Naming:
- `snake_case` ашиглах.
  ```
  GET /api/users/{id}
  POST /api/auth/login
  ```

### 3. Error Response Structure:
- Нэгдсэн JSON бүтэц буцаах:
  ```json
  {
    "success": false,
    "message": "User not found",
    "error_code": 404
  }
  ```

## Git Стандарт

### 1. Коммит мэссеж:
- Дараах бүтэц мөрдөх: `type(scope): short description`
- **Төрөлүүд**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.
  ```
  feat(auth): add user authentication module
  ```

### 2. Салаа мөчир нэрлэх:
- **Feature**: `feature/add-user-auth`
- **Bugfix**: `bugfix/fix-login-error`
- **Hotfix**: `hotfix/fix-crash-on-login`

### 3. Репозитор үүсгэх:
- Ойлгомжтой тайлбарласан `README.md` файл оруулах.

---

Энэхүү стандарт нь Blueprint Solutions LLC-ийн бүх төслүүдэд мөрдөгдөж, хөгжүүлэлтийн чанар, үр ашгийг нэмэгдүүлэх үндсэн баримт бичиг болно.
