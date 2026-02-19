# API Test Scenarios – password recovery

## Objective
Memvalidasi respons dan kontrol akses pada endpoint password recovery melalui pendekatan black-box testing, dengan fokus pada:

- Keamanan lifecycle token
- Pencegahan account enumeration
- Penegakan password policy di sisi server
- Konsistensi invalidasi session
- Konsistensi response time

## Endpoints Assumed

POST /auth/forgot-password  
POST /auth/reset-password  
POST /auth/login

