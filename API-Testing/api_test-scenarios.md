# API Test Scenarios – password recovery

## Objective
Memvalidasi perilaku backend pada mekanisme reset password dengan fokus pada:

- Keamanan lifecycle token
- Pencegahan account enumeration
- Penegakan password policy di sisi server
- Konsistensi invalidasi session
- Konsistensi response time

## Endpoints Assumed

POST /auth/forgot-password  
POST /auth/reset-password  
POST /auth/login

