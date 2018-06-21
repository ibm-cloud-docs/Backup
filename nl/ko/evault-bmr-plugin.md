---

copyright:
  years: 1994, 2018
lastupdated: "2018-06-18"

---
{:new_window: target="_blank"}

# EVault BMR(Bare Metal Restore) 플러그인 설치

EVault BMR은 운영 체제나 하드웨어 장애 등의 재해가 발생할 때 베어메탈 상태에서 서버를 완전히 복원할 수 있도록 하는 Microsoft Windows용 재해 복구 솔루션입니다. 이 시스템을 사용하면 {{site.data.keyword.BluSoftlayer_full}}에서 관리하는 안전한 보안 위치에서 시스템 이미지를 빠르게 복원할 수 있습니다.

**참고**: BMR은 실제 서버의 Microsoft Windows 전용 제품입니다. 이는 가상 서버에는 사용할 수 없습니다. Linux용 BMR(Bare Metal Restore) 배포는 지원되지 않습니다. EVault Agent 8.30 이하에서만 BMR을 지원합니다. (2018년 6월 30일).

## 제공되는 기능

- 선택된 특정 시점으로 시스템을 복원합니다.
- 이미지 또는 파일 기반 백업에서 시스템을 복원합니다.
- EVault에 저장된 백업에서 시스템을 복원합니다.
- 부트 가능한 시스템이 없어도 데이터를 복원할 수 있도록 하는 실행 가능한 복구 트랜잭션.

## 플러그인 주문

1. [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}에 로그인하십시오.
2. **스토리지** > **백업**을 클릭하십시오.
3. EVault 계정을 선택하고 **플러그인 주문**을 클릭하십시오.
4. **EVault 플러그인 - BMR(Bare Metal Restore)**을 선택하고 **계속**을 클릭하십시오.
5. 프로모션 코드가 있으면 이를 입력하고 **재계산**을 클릭하십시오.
6. 업데이트된 비용이 표시됩니다. 주문을 검토하십시오.  
7. 상자를 선택하여 마스터 서비스 계약을 읽고 써드파티 소프트웨어 이용 약관에 동의함을 표시하십시오.  
8. **주문하기**를 클릭하십시오.

## 사용자 가이드

[다운로드 가능한 EVault 문서](http://downloads.service.softlayer.com/evault/Documentation/){:new_window}에서 EVault System Restore v8.3 - User Guide.pdf를 다운로드할 수 있도록 {{site.data.keyword.BluVPN}}의 {{site.data.keyword.BluSoftlayer_full}} 네트워크에 연결하십시오.

## 자주 묻는 질문(FAQ)

### 단일 디스크에서 RAID 어레이로 마이그레이션할 수 있습니까?

예, 그렇습니다. 그러나 RAID 어레이로 인해 크기가 감소되므로 대용량 디바이스를 선택해야 합니다.

### 원래 볼륨보다 큰 디스크로 이미지를 복원하면 어떻게 됩니까?

원래 볼륨보다 큰 디스크로 이미지를 복원하면 남은 공간이 할당 해제됩니다. 따라서 예를 들어 500GB 드라이브가 있으며 1TB 디스크로 해당 데이터를 복원하면 500GB의 디스크 공간이 할당 해제됩니다. Windows 2008에서는 고유 디스크 유틸리티를 사용하여 기본 파티션을 늘릴 수 있습니다. 그러나 Windows 2003에서는 이와 관련된 기본 기능이 없으므로 단순히 영역을 할당하도록 권장합니다.

### 내 일반 백업에 BMR을 사용할 수 있습니까?

이는 디스크 이미지가 아니라 시스템 볼륨 이미지 백업 시스템입니다. 이 시스템은 일반 백업 용도는 아니지만 이와 함께 사용됩니다.   

### 내 데이터베이스 백업에 BMR을 사용할 수 있습니까?

데이터베이스 백업은 일반 EVault 백업 방법과는 별도로 수행되어야 합니다. BMR이 있어도 SQL 또는 Oracle 플러그인은 여전히 필요합니다. BMR이 VSS 기술을 사용하여 오픈 파일을 백업하지만, 백업 파일의 트랜잭션 일관성을 항상 보장할 수는 없습니다. 이러한 유형의 특수 애플리케이션에 대해 두 개의 백업 작업을 작성하도록 권장합니다(하나는 OS 및 애플리케이션 2진 파일 백업용이며 다른 하나는 애플리케이션 데이터용임). BMR 사용자 안내서의 맨 뒤쪽에 이러한 영향에 대한 설명이 있습니다.

### BMR에서 어떤 유형의 복원 작업을 수행할 수 있습니까?

전체 시스템 복원을 수행하거나 복원할 백업에서 개별 파일을 선정할 수 있습니다. 이는 이 작업이 현재 파일 백업 작업을 대체할 수 있음을 의미합니다. 복원 프로세스는 기존의 백업 작업처럼 OS 내에서 수행될 수 있습니다.

### BMR에 오픈 파일 백업 기능이 있습니까?

BMR에는 오픈 파일 백업 기능이 있습니다. 그러나 BMR이 있어도 SQL 또는 Oracle 플러그인은 여전히 필요합니다. MSSQL 플러그인 설치 지시사항을 보려면 [여기를](evault-mssql-plugin.html) 클릭하십시오.

### BMR 복원에 필요한 디스크 공간과 시간은 얼마나 됩니까?

기본 설치에서 작성된 백업은 약 6GB를 사용합니다. 이러한 복원은 1GB 포트에서 약 15분 정도 걸립니다. 이 프로세스는 개인용 포트 속도의 영향도 받습니다. 보다 빠른 백업/복원이 필요하면 포트 속도를 늘려야 할 수 있습니다.