# Vercel 배포 가이드

## 🚀 3단계 배포 과정

### Step 1: Vercel 계정 생성

1. https://vercel.com 접속
2. **Continue with GitHub** 클릭
3. GitHub 계정으로 로그인

### Step 2: 로컬에서 배포

```bash
# 배포 스크립트 실행
cd /root/clawd
bash scripts/deploy_vercel.sh
```

### Step 3: Vercel 도메인 확인

배포가 완료되면 자동 도메인 발급:
```
https://jarvis-dashboard-xxxxx.vercel.app
```

---

## 🌐 도메인 설정 (선택)

### Vercel 무료 도메인
```
자동 생성: your-project.vercel.app
```

### 커스텀 도메인
1. 도메인 구매 (약 1~2만원/년)
   - 가비아, 닷네임, 후이즈 등
2. Vercel 대시보드 → Settings → Domains
3. 도메인 입력 후 DNS 설정 안내 따름

---

## ⚙️ 내가 알려줘야 하는 것

### 1. Vercel 프로젝트 이름 (선택)
기본값: `jarvis-dashboard`
원하면 변경 가능

### 2. 배포 범위
```
? Set up and deploy “~/clawd/vercel-dist”? [Y/n]
```
→ **Y** 입력

### 3. 링크할 프로젝트 (선택)
```
? Link to existing project? [y/N]
```
→ 첫 배포는 **N**

---

## 🔧 필요한 설정

### 로컬 서버 (이미 완료 ✅)
- [x] API 서버 실행 (포트 8081)
- [x] 방화벽 허용
- [x] CORS 설정

### Vercel 측 (자동 처리)
- vercel.json 설정
- 정적 파일 배포
- API 프록시

---

## 📋 배포 후 체크리스트

### Vercel 대시보드 확인
1. https://vercel.com/dashboard 접속
2. 프로젝트 상태 확인
3. 도메인 확인

### 대시보드 접속 테스트
```
https://your-project.vercel.app/dashboard.html
```

### API 연결 테스트
- 작업 목록 표시되는지 확인
- 실시간 갱신 작동하는지 확인

---

## ⚠️ 중요提醒

### 로컬 서버 유지
Vercel은 **프론트엔드만** 배포합니다.
API는 로컬 서버가 계속 실행되어야 합니다.

### API 서버 자동 실행
```bash
# PM2로 영구 실행
npm install -g pm2
pm2 start /root/clawd/scripts/dashboard_api.py --name dashboard-api
pm2 save
pm2 startup
```

---

## 🆘 문제 해결

### 배포 실패
```bash
# �시 삭제 후 재배포
rm -rf vercel-dist/.vercel
bash scripts/deploy_vercel.sh
```

### API 연결 안 됨
1. 로컬 서버 상태 확인
2. 포트 8081 확인
3. 방화벽 확인

---

## 📞 도움이 필요하면

1. 배포 시작 전에 알려주세요
2. 프로젝트 이름 원하시는 대로 정해주세요
3. 도메인 필요하시면 말씀해주세요
