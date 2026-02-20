# Test Plan – Password Recovery

## 1. Objective
Memastikan fitur Password Recovery memungkinkan user memulihkan akses akun secara aman, konsisten, dan terkontrol.

## 2. Scope
Pengujian mencakup :
- Forgot password request
- Email reset link behavior
- Token validation & expiration
- Password update process
- Session invalidation setelah reset

## 3. Out of Scope
- Implementasi enkripsi password di backend
- Konfigurasi SMTP dan deliverability email
- Rate limiting dan brute force protection tingkat infrastruktur
- Detail implementasi hashing token

## 4. Test Approach
- Black-box testing
- Functional testing
- Negative testing
- Security-oriented validation (basic authentication boundary checks)
- UI verification dan API verification

## 5. Test Environment
- Browser: Firefox 147.0.3
- OS: Windows 10
- Backend: Simulated / Dummy system
  
## 6. Deliverables
- Test Scenarios
- Test Cases
- API Test Documentation
- Risk Analysis
- Bug Report
