---
title: Adobe Identity Management으로 마이그레이션
description: 설명 곧 제공될 예정입니다.
role: User
level: Beginner
hide: true
hidefromtoc: true
feature: Marketing
exl-id: 8368a148-c0c8-462f-b166-9efc412c4a0f
source-git-commit: f6ae52b43770789c24237f0bc664d33541469a50
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---

# Adobe Identity Management으로 마이그레이션

Adobe을 통해 Adobe Marketo Engage 구독 및 사용자를 관리하는 방법을 향상시킬 수 있습니다. Marketo Engage 구독과 사용자를 Adobe Admin Console으로 마이그레이션하여 귀하와 귀하의 조직에 향상된 생산성을 제공하고 있습니다.

이 자습서를 통해 마이그레이션을 탐색하여 중앙 위치에서 사용자의 다른 Adobe 계정 및 제품과 함께 Adobe Marketo Engage을 관리할 수 있습니다. 마이그레이션이 필요하며 마케팅 워크플로우, 콘텐츠, 통합 또는 자산에 영향을 주지 않습니다.

## Marketo Engage 관리자를 위한 마이그레이션 전 확인 목록 {#pre-migration-checklist-for-marketo-engage-administrators}

조직에서 Adobe Marketo Engage을 Adobe Admin Console으로 마이그레이션할 수 있도록 아래 체크리스트에 따라 예정된 변경 사항을 관리하는 것이 좋습니다.

### 1. 시스템 관리자를 식별하고 필요한 조치를 논의합니다 {#identify-your-system-administrators}

* 조직 내 시스템 관리자를 모르는 경우 Adobe 계정 팀에 문의하거나 Adobe 지원 `marketocares@marketo.com`에 문의하십시오.

* Marketo Engage 구독을 마이그레이션할 Adobe Admin Console(또는 Adobe 조직)를 확인합니다.  Marketo Engage 구독은 Marketo Engage과 통합된 기본 대화 자동화 도구인 Dynamic Chat과 동일한 조직에 배포되어야 합니다.
  `TBD LINK TO https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/understanding-marketo-subscription-and-user-migration-to-the-adobe-admin-console#subscription-migration-complete`

* [샘플 전자 메일 섹션](#announce-the-migration-timeline)에서 시스템 관리자와 통신하는 방법에 대해 자세히 알아보세요.

### 2. Adobe ID로 마이그레이션하는 경우의 변경 사항과 영향에 대해 숙지하십시오 {#familiarize-yourself-with-the-changes}

아래 비디오에서는 Marketo Engage 제품 관리 팀이 마이그레이션 여정과 예상 내용을 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3430920t3/?quality=12&learn=on){transcript=true}

Marketo Engage 관리자를 위한 이 항목에 대한 자세한 내용은 다음 도움말 문서에서 확인할 수 있습니다.

* [사용자 설정 검사 목록](https://experienceleague.adobe.com/en/docs/marketo/using/getting-started/initial-setup/user-setup){target="_blank"}

* [Adobe Identity Management 개요](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/adobe-identity-management-overview){target="_blank"}

* [Marketo 구독 및 Adobe Admin Console으로의 사용자 마이그레이션 이해](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/understanding-marketo-subscription-and-user-migration-to-the-adobe-admin-console){target="_blank"}

* [마이그레이션 콘솔을 사용하여 Adobe ID로 마이그레이션](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/migrating-to-adobe-identity){target="_blank"}

* [Adobe Admin Console 사용 방법 이해](https://helpx.adobe.com/enterprise/using/admin-console.html){target="_blank"}

### 3. 내부 팀에 필요한 마이그레이션 타임라인 및 준비 상황을 알려줍니다 {#announce-the-migration-timeline}

* 예약되면 Marketo Engage 관리자 및 사용자 달력에 마이그레이션 날짜를 표시합니다.

내부 타임라인에 더 잘 부합하도록 **관리자** > **마이그레이션 콘솔** > **사전 마이그레이션**&#x200B;에서 마이그레이션 날짜를 수정할 수 있습니다. 일정 조정 및 [마이그레이션 날짜 수정](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/migrating-to-adobe-identity#pre-migration){target="_blank"}의 제한 사항에 대해 자세히 알아보세요.

* 시스템 관리자와 소통하려면 이메일을 보내십시오.

다음은 시스템 관리자에게 보낼 샘플 이메일입니다. 일반적으로 IT 부서에서 모든 Adobe 라이센스를 관리합니다.

`---------------------------------------------------`

**제목: 지원 필요—Adobe Admin Console에 대한 Marketo Engage 구독 마이그레이션**

`[IT Administrator/NAME]`님,

Marketo Engage 구독이 곧 Adobe Identity Management 시스템으로 마이그레이션됩니다. [마케팅 운영 팀]은(는) Marketo Engage 사용자에게 미치는 영향을 최소화하기 위해 사용자 마이그레이션이 시작되기 전에 필요한 몇 가지 단계를 완료하는 데 도움이 필요합니다.

`1.` 조직에서 이미 Adobe Admin Console의 다른 Adobe 제품을 관리하는지, Marketo Engage이 동일한 콘솔로 마이그레이션되는지 확인합니다.

* Marketo Engage 구독은 Marketo Engage과 통합된 기본 대화 자동화 도구인 Dynamic Chat과 동일한 조직에 있어야 합니다.

* Marketo Engage을 추가할 Admin Console에 대한 우려 사항이나 질문이 있는 경우 `marketocares@marketo.com`의 지원 팀에 연락하여 커뮤니케이션에 포함시켜 주십시오.

`2.` 제목란 &quot;Adobe Marketo Engage `[Package Tier]`에 대한 사용자 액세스를 관리하는 데 필요한 작업&quot;을 사용하여 Adobe에서 전자 메일을 확인합니다. 이 이메일은 Admin Console에 Marketo Engage 라이선스가 프로비저닝된 후 전송되었습니다. 시스템 관리자만 이 이메일을 수신하게 됩니다. 수령하시면 즉시 알려주시기 바랍니다.

* Adobe은 Admin Console을 조직의 기존 콘솔로 자동으로 마이그레이션하기 위해 사용자의 시스템 관리자인 사용자의 동의를 구할 수 있습니다. 제목이 &quot;Adobe Marketo Engage `[Package Tier]`에 대한 사용자 액세스를 관리하는 데 필요한 작업&quot;인 전자 메일에서 &quot;시작하기&quot; 버튼을 클릭하여 동의 페이지로 이동합니다.

`3.` **선택 사항:** Adobe Admin Console에서 SSO(Single Sign-On) 설정.

* 앞으로 Adobe ID에서 SSO로 로그인할 수 있도록 사용자를 마이그레이션하기 전에 Adobe Admin Console에서 SSO 설정을 지원하도록 요청합니다.
전환기에 협조해 주셔서 감사합니다. Marketo Engage으로 사용자 마이그레이션을 진행할 수 있도록 이 단계를 완료하면 알려 주십시오.
감사합니다.

`[Your Name]`

`---------------------------------------------------`

* Marketo Engage 사용자에게 이메일을 보냅니다.

다음은 관리자 권한이 없는 Marketo Engage 사용자에게 예정된 마이그레이션을 알리는 데 사용할 수 있는 샘플 이메일입니다.

`---------------------------------------------------`

**제목: 중요 업데이트—Adobe Admin Console에 대한 Marketo Engage 구독 마이그레이션**

Marketo Engage 사용자님께,

Marketo Engage 인스턴스 및 로그인 방법에 관한 중요한 발표가 있습니다. Adobe은 고객이 한 곳에서 모든 제품 관리를 중앙 집중화할 수 있도록 Marketo Engage 구독 및 사용자를 Adobe Admin Console으로 이동하고 있습니다. 마케팅 워크플로우, 콘텐츠, 통합 또는 자산에는 영향을 주지 않습니다.

주요 세부 사항:

* 마이그레이션 날짜: [예약된 날짜를 지정하십시오. - **관리자** > **마이그레이션 콘솔** > **마이그레이션 전**] 아래의 Marketo Engage에서 찾으십시오.

* 시간: 현지 시간으로 자정에 구독을 시작해 마이그레이션합니다.

* 영향: 사용자 마이그레이션 중에 제품 액세스 손실이 발생하지 않습니다. 계정이 마이그레이션될 때 로그인하면 로그아웃되고 마이그레이션 후 Adobe ID를 사용하여 몇 분 안에 다시 로그인하라는 메시지가 표시됩니다.

* 이점: Adobe ID 또는 SSO(Adobe Federated ID)인 단일 Adobe ID를 사용하여 Marketo Engage 및 기타 Adobe 제품을 인증합니다.

필요한 작업:

`1.` 준비: Adobe ID로 마이그레이션하려면 전자 메일 확인이 필요합니다.

i. 링크가 포함된 이메일 확인 요청 이메일을 받았습니다(3일 동안 유효). 링크가 만료된 경우 **관리자** > **내 계정** > **계정 설정**&#x200B;으로 이동하여 **확인 다시 보내기**를 클릭하여 확인 전자 메일을 다시 보낼 수 있습니다.
아.. 전자 메일 확인이 성공하려면 활성 사용자 세션이 필요합니다. 먼저 ID 공급자(IdP) URL을 사용하여 Marketo Engage 구독에 로그인하십시오.

`2.` 온보드: 사용자 계정이 마이그레이션되면 로그인 방법 변경 사항과 관련된 전자 메일이 Adobe에게 전송됩니다.

i. &#39;초대 수락&#39; 버튼을 클릭하고 Adobe ID를 사용하여 로그인함으로써 새 초대를 수락합니다.
아.. Adobe 로그인 페이지에서 기존 Adobe ID으로 로그인하십시오.

`3.` 연락처: 계정을 마이그레이션한 후 질문이 있거나 도움이 필요한 경우 또는 계정이 마이그레이션되지 않았으며 Marketo Engage에 대한 액세스 권한이 없는 경우 [내부 연락처 전자 메일/전화]의 Marketo Engage 마이그레이션 팀에 문의하세요.

전환기에 협조해 주셔서 감사합니다. 시스템을 안전하게 유지하기 위한 귀사의 이해와 헌신에 감사드립니다.

우수 사례,

[내 이름]

`---------------------------------------------------`
