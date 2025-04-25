## 개요

Realtek RTL8111/8168/8411 이더넷 컨트롤러 (rev 2b)를 사용하는 원격 PC에 Proxmox 8을 설치하고 유선 인터넷을 연결하기 위한 도구입니다.

문제 상황:

- Debian 12 설치 시 Realtek RTL8111/8168/8411 드라이버(r8168)가 포함되어 있지 않음
- Proxmox 8 설치 시 무선 인터넷 연결을 위한 패키지가 포함되어 있지 않음

따라서 무선 인터넷 연결이 가능한 Debian 12 환경에서
Proxmox 8의 커널과 패키지를 설치한 뒤 
커널 버전에 맞는 r8168 드라이버를 적용하여 유선 인터넷을 사용할 수 있도록 하였습니다.

## 요구사항

### 로컬

- Ansible, Make 설치

### 원격

- Debian 12 설치
- 정적 IP 설정
- 무선 인터넷 연결 (원격 설치를 위해 필요)

## 디렉토리 구조

```
initial_setup/
├── Makefile			# 실행을 위한 Makefile
├── ansible/
│   ├── ansible.cfg		# Ansible 설정 파일
│   ├── site.yml		# 메인 플레이북
│   └── roles/			# Ansible Role
│       ├── network/	# 네트워크 설정 Role
│       └── proxmox/	# Proxmox 설치 Role
```

## 사용 방법

다음 명령어를 통해 실행:

```bash
make USER=username HOST=xx.xx.xx.xx
```

이후 작업 완료와 함께 유선 인터넷이 연결됩니다.

## 참고 자료

- [Install Proxmox VE on Debian 12 Bookworm](https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_12_Bookworm)
- [Realtek r8168 Driver for Proxmox VE Kernel version 6.8](https://gist.github.com/tushroy/69f84ee5955e76396f3b0f41ad9b731a)
