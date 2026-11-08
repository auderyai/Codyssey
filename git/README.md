# 1. Git & GitHub 설정 및 연동 실습

프로젝트의 버전 관리와 효율적인 협업을 위해 로컬 Git 환경을 설정하고 GitHub 원격 저장소와 연동을 완료했습니다.

### 1.1 Git 로컬 환경 설정
사용자 식별 정보 등록 및 기본 브랜치 전략, 자격 증명 관리 방식을 설정했습니다.

- **주요 설정 내역**:
  - **사용자 정보**: `auderyai` / `auderyai62@gmail.com`
  - **기본 브랜치**: `main` (기존 master에서 변경)
  - **자격 증명 도우미**: `store` (매번 로그인하는 번거로움 해결)
  - **원격 저장소**: `https://github.com/auderyai/Codyssey.git` 연결 확인

![Git 설정 확인](img/git-01-config.png)

### 1.2 VS Code & GitHub 계정 연동
IDE 환경에서 원활한 소스 제어를 위해 VS Code와 GitHub 계정을 연동했습니다.

- **연동 결과**: 
  - `auderyai` 계정 로그인 완료
  - 설정 동기화(Settings Sync) 활성화로 개발 환경 일관성 유지
![VS Code 연동 확인](img/git-02-vscode-auth.png)

---
**💡 학습 포인트**: `git config --list`를 통해 현재 프로젝트에 적용된 모든 설정(로컬/글로벌)을 한눈에 파악할 수 있으며, `remote.origin.url`을 통해 올바른 저장소에 연결되었는지 검증하는 과정이 중요함을 배웠습니다.

## 🔐 Git SSH 인증 설정_보너스 선택

보안 강화 및 자동 로그인을 위해 SSH 프로토콜을 설정하였습니다.

### 1. SSH 키 생성 (Key Generation)
최신 보안 알고리즘인 `ed25519`를 사용하여 키 쌍을 생성했습니다.
- **명령어**: `ssh-keygen -t ed25519 -C "auderyai62@gmail.com"`
- **저장 경로**: `/root/.ssh/id_ed25519`

![SSH 키 생성](./img/git-01-ssh-keygen.png)

### 2. GitHub 연결 확인 및 원격 저장소 변경
생성한 공개키를 GitHub에 등록한 후, 서버와 GitHub 간의 연결을 확인하고 기존 HTTPS 주소를 SSH 주소로 변경했습니다.

- **연결 테스트**: `ssh -T git@github.com`
- **주소 변경**: `git remote set-url origin git@github.com:auderyai/Codyssey.git`

![SSH 연결 및 주소 변경](./img/git-02-ssh-remote.png)

---

### 💡 핵심 요약
1. **비대칭키 원리**: 서버에는 공개키(`.pub`)를 두고, 내 로컬(Platinum 서버)에는 개인키를 보관하여 인증합니다.
2. **효율성**: 이제 `git push` 시 매번 아이디와 비밀번호(또는 Token)를 입력할 필요가 없습니다.
3. **보안**: HTTPS보다 탈취 위험이 적고 안전한 통신이 가능합니다.