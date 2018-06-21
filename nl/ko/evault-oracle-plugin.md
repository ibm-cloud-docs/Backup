---

copyright:
  years: 1994, 2018
lastupdated: "2018-06-06"

---
{:new_window: target="_blank"}

# EVault Oracle 플러그인 설치

Oracle 플러그인은 Oracle 데이터베이스 호스트에서 Windows 에이전트로 설치됩니다. WebCC 포털을 사용하여 작업을 구성하고 안전한 원격 저장소에 Oracle 데이터베이스를 백업하며 Oracle 데이터베이스를 복원할 수 있습니다. Oracle 플러그인은 기존 아키텍처로 통합됩니다. 

## 제공되는 기능

- Oracle 데이터베이스 백업 및 복구 지원. 
- Oracle 플러그인은 전체 온라인 데이터베이스 인스턴스의 ARCHIVELOG 기반, 비-RMAN 백업을 제공합니다. 모든 비-임시 테이블스페이스와 인스턴스 매개변수 파일은 자동으로 백업됩니다. Oracle Corporation에서는 데이터베이스 작업이 뜸한 기간에 백업을 받도록 권장합니다. 
- 전체 및 부분 데이터베이스는 보통의 사용자 관리되는 Oracle 복구 메커니즘을 통해 복원됩니다. 

## 플러그인 주문

1. [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}에 로그인하십시오. 
2. **스토리지** > **백업**을 클릭하십시오. 
3. EVault 계정을 선택하고 **플러그인 주문**을 클릭하십시오. 
4. **EVault 플러그인 - Oracle**을 선택하고 **계속**을 클릭하십시오. 
5. 프로모션 코드가 있으면 이를 입력하고 **재계산**을 클릭하십시오. 
6. 업데이트된 비용이 표시됩니다. 주문을 검토하십시오.  
7. 상자를 선택하여 마스터 서비스 계약을 읽고 써드파티 소프트웨어 이용 약관에 동의함을 표시하십시오.  
8. **주문하기**를 클릭하십시오. 

## Oracle 플러그인 설치

Windows용 Oracle 플러그인은 32비트 또는 64비트 Windows 에이전트로 설치됩니다. Windows용 Oracle 플러그인을 설치하려면 에이전트 설치 킷을 실행하십시오. Oracle 플러그인은 **사용자 설치** 페이지에서 옵션으로 나타납니다. 

**참고**: Microsoft Windows 서버용 플러그인을 설치하기 전에 `services.msc`에서 두 EVault 서비스를 모두 중지하십시오.   

1. `c:\installs\evault` 폴더를 찾아보고 상위 개정 번호로 .exe 파일을 실행하십시오. 
2. 언어 화면에서 **확인**을 클릭하십시오. 
3. 시작 화면에서 **다음**을 클릭하십시오. 
4. **설치 수정**을 선택하고 **다음**을 클릭하십시오. 
5. **미변경 상태 유지**를 선택하고 **다음**을 클릭하십시오. 
6. 사용자 설치 화면에서 구매한 각 플러그인을 선택하고 **이 기능이 설치될 위치...**를 선택한 후에 **다음**을 클릭하십시오. 
7. **내 현재 등록 유지** 단일 선택 단추를 선택하고 **다음**을 클릭하십시오. 
8. **설치**를 클릭하십시오. 
9. 일단 설치되면 두 서비스가 모두 사용되고 실행 중인지 확인하십시오. 
10. WebCC에서 데이터베이스 액세스(보기)가 가능하면 설치가 완료된 것입니다.  

## 사용자 가이드

[다운로드 가능한 EVault 문서](http://downloads.service.softlayer.com/evault/Documentation/){:new_window}에서 EVault Agent v8.0 for Microsoft Windows - Oracle Plug-in Guide.pdf를 다운로드할 수 있도록 {{site.data.keyword.BluVPN}}의 {{site.data.keyword.BluSoftlayer_full}} 네트워크에 연결하십시오. 

## 자주 묻는 질문(FAQ)

### Oracle 플러그인의 제한사항은 무엇입니까? 
- 로컬, 단일 인스턴스, 디스크 기반 데이터베이스만 백업됩니다. 
- 데이터베이스 클러스터는 백업되지 않습니다. 
- 원시 디바이스는 백업되지 않습니다. 
- 원격 데이터베이스는 백업되지 않습니다. 
- 데이터베이스는 ARCHIVELOG 모드에서 실행되어야 하며, 백업이 구성된 사용자에게 SYSDBA 권한이 있어야 합니다. 
- 데이터베이스 비밀번호는 스크립트 기반 메소드에서 보안성 강화를 위해 암호화됩니다. 