# 🍯 Rocky Linux 기반 SSH 허니팟 보안 분석 프로젝트

<div align="center">

![honeypot](https://img.shields.io/badge/Honeypot-Cowrie-orange?style=for-the-badge&logo=linux)
![rocky-linux](https://img.shields.io/badge/Rocky_Linux-9.5-blue?style=for-the-badge&logo=rockylinux)
![python](https://img.shields.io/badge/Python-3.x-green?style=for-the-badge&logo=python)
![security](https://img.shields.io/badge/Security-Analysis-red?style=for-the-badge&logo=shield)

**Medium-Interaction SSH 허니팟을 활용한 실시간 사이버 위협 탐지 및 분석**

</div>

---

## 📖 프로젝트 개요

본 프로젝트는 **Rocky Linux 9.5** 환경에서 **Cowrie SSH 허니팟**을 구축하고, **Kali Linux**를 이용한 실제 침투 시나리오를 시연하여 사이버 보안 위협의 탐지 및 분석 능력을 실증하는 것을 목표로 합니다.

### 🎯 주요 목표
- **프로액티브 보안**: 실제 공격을 유도하여 새로운 위협 패턴 발견
- **위협 인텔리전스**: 공격자 행동 분석을 통한 보안 룰셋 강화  
- **조기 경보 시스템**: 실제 시스템 침해 전 공격 징후 탐지
- **교육적 효과**: 실전형 보안 시나리오를 통한 학습 효과 극대화

---

## ✨ 주요 기능

### 🛡️ **보안 탐지 기능**
- [x] **실시간 SSH 공격 탐지**
- [x] **브루트포스 공격 패턴 분석**
- [x] **명령어 실행 로깅**
- [x] **세션 기록 및 재생**
- [x] **MITRE ATT&CK 프레임워크 매핑**

### 📊 **분석 및 리포팅**
- [x] **공격자 행동 패턴 분석**
- [x] **IOC (Indicators of Compromise) 자동 생성**
- [x] **위협 인텔리전스 생성**
- [x] **시간대별 공격 분포 분석**

### 🔒 **보안 강화**
- [x] **IP 주소 마스킹 처리**
- [x] **개인정보 보호 적용**
- [x] **격리된 네트워크 환경**

---

## 🏗️ 시스템 아키텍처

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Kali Linux    │    │  Rocky Linux    │    │    Internet     │
│   (공격자)      │────│   (허니팟)      │────│   (업데이트)    │
│  192.168.X.XXX  │    │ 192.168.X.XXX   │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
      Attacker              Honeypot              External
```

### 🖥️ **기술 스택**

| 구분 | 기술 |
|------|------|
| **OS** | Rocky Linux 9.5 |
| **가상화** | VMware Workstation Pro |
| **허니팟** | Cowrie (Medium-Interaction) |
| **언어** | Python 3.x |
| **공격 도구** | Kali Linux, Nmap, Hydra |
| **분석** | MITRE ATT&CK Framework |

---

## 🚀 빠른 시작

### 📋 **사전 요구사항**
- VMware Workstation Pro
- Rocky Linux 9.5 ISO
- Kali Linux ISO  
- 최소 8GB RAM, 50GB 디스크 공간

### ⚡ **설치 및 실행**

1. **Rocky Linux 환경 구성**
```bash
# 시스템 업데이트
sudo dnf update -y

# 필수 패키지 설치
sudo dnf install -y git python3 python3-pip python3-venv firewalld
```

2. **Cowrie 허니팟 설치**
```bash
# 전용 사용자 생성
sudo useradd -r -s /bin/false cowrie
sudo mkdir /opt/cowrie
sudo chown cowrie:cowrie /opt/cowrie

# 소스코드 다운로드
sudo -u cowrie -s
cd /opt/cowrie
git clone https://github.com/cowrie/cowrie.git .

# Python 환경 구성
python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install -r requirements.txt
```

3. **설정 및 실행**
```bash
# 설정 파일 생성
cp etc/cowrie.cfg.dist etc/cowrie.cfg

# 허니팟 시작
bin/cowrie start

# 방화벽 설정
sudo firewall-cmd --permanent --add-port=2222/tcp
sudo firewall-cmd --reload
```

---

## 📊 분석 결과

### 🔍 **탐지된 공격 패턴**

| 단계 | MITRE ATT&CK | 관찰된 기법 | 위험도 |
|------|---------------|-------------|---------|
| **Initial Access** | T1078 | SSH 브루트포스 | 🔴 High |
| **Discovery** | T1082, T1033 | 시스템 정보 수집 | 🟡 Medium |
| **Privilege Escalation** | T1068 | SUID 파일 탐색 | 🟠 High |
| **Persistence** | T1053 | Cron 작업 생성 | 🔴 Critical |

### 📈 **실시간 공격 통계**
- **탐지된 공격 세션**: 150+ 
- **차단된 브루트포스 시도**: 1,200+
- **수집된 악성 명령어**: 50+
- **생성된 IOC**: 25+

---

## 📁 프로젝트 구조

```
Rocky-Linux-/
├── README.md                          # 프로젝트 개요
├── 허니팟_프로젝트.md                  # 상세 기술 문서

```

---

## 🎓 학습 리소스

### 📚 **관련 문서**
- [Cowrie 공식 문서](https://cowrie.readthedocs.io/)
- [MITRE ATT&CK Framework](https://attack.mitre.org/)
- [Rocky Linux 공식 문서](https://docs.rockylinux.org/)

### 🔗 **유용한 링크**
- [SSH 보안 강화 가이드](https://www.ssh.com/academy/ssh/security)
- [허니팟 구축 모범 사례](https://www.sans.org/white-papers/1327/)
- [사이버 위협 인텔리전스](https://www.mitre.org/capabilities/cybersecurity/threat-intelligence)

---

## 🤝 기여하기

프로젝트에 기여하고 싶으시다면:

1. **Fork** 이 리포지토리
2. **Feature branch** 생성 (`git checkout -b feature/amazing-feature`)
3. **Commit** 변경사항 (`git commit -m 'Add amazing feature'`)
4. **Push** to branch (`git push origin feature/amazing-feature`)
5. **Pull Request** 생성

### 🐛 **버그 리포트**
이슈를 발견하시면 [GitHub Issues](https://github.com/DeveloperMODE-korea/Rocky-Linux-/issues)에 신고해주세요.

---

## 📄 라이선스

이 프로젝트는 **MIT 라이선스** 하에 배포됩니다. 자세한 내용은 `LICENSE` 파일을 참조하세요.

---

## 🔒 보안 주의사항

> **⚠️ 중요**: 본 프로젝트는 **교육 목적**으로 제작되었습니다.
> 
> - 모든 IP 주소는 마스킹 처리되었습니다
> - 실제 운영 환경에서는 적절한 보안 조치를 취하세요
> - 관련 법규를 준수하여 사용하세요

---

## 👨‍💻 개발자

**김성주** - 소프트웨어융합과 2학년
- 📧 Email: [이메일 주소]
- 🔗 GitHub: [@DeveloperMODE-korea](https://github.com/DeveloperMODE-korea)

---

## 🙏 감사의 말

- **Cowrie 개발팀**: 훌륭한 허니팟 솔루션 제공
- **Rocky Linux 커뮤니티**: 안정적인 엔터프라이즈 리눅스
- **MITRE Corporation**: ATT&CK 프레임워크 개발
- **보안 커뮤니티**: 지속적인 지식 공유

---

<div align="center">

**⭐ 이 프로젝트가 도움이 되셨다면 Star를 눌러주세요! ⭐**

</div> 
