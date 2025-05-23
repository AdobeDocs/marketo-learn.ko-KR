---
title: Adobe Identity Management으로 마이그레이션
description: 이 자습서는 Marketo Engage 구독 및 사용자를 Adobe Admin Console으로 마이그레이션하는 작업을 탐색하는 데 도움이 됩니다.
role: Admin
level: Intermediate, Experienced
recommendations: noDisplay, noCatalog
last-substantial-update: 2024-07-26T00:00:00Z
feature: Marketing
exl-id: 8368a148-c0c8-462f-b166-9efc412c4a0f
source-git-commit: dcfffa299cbcfef489f5b618fae29f745b878d26
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 0%

---

# Adobe Identity Management으로 마이그레이션

Adobe은 Adobe Marketo Engage 구독 및 사용자를 관리하는 방법을 개선하고 있습니다. Marketo Engage 구독과 사용자를 Adobe Admin Console으로 마이그레이션하여 조직의 생산성을 높이고 있습니다.

이 자습서는 마이그레이션을 탐색하여 중앙 위치에서 사용자에 대한 다른 Adobe 계정 및 제품과 함께 Adobe Marketo Engage 관리를 시작할 수 있도록 도와줍니다. 마이그레이션이 필요하며 마케팅 워크플로우, 콘텐츠, 통합 또는 자산에 영향을 주지 않습니다.

## Marketo Engage 관리자를 위한 마이그레이션 전 검사 목록 {#pre-migration-checklist-for-marketo-engage-administrators}

조직에서 Adobe Marketo Engage을 Adobe Admin Console으로 마이그레이션할 수 있도록 아래 체크리스트에 따라 예정된 변경 사항을 관리하는 것이 좋습니다.

### 1. 시스템 관리자 및 IT 팀을 식별하고 필요한 조치를 논의합니다 {#identify-your-system-administrators}

* 조직 내 시스템 관리자를 모르는 경우 Adobe 계정 팀에 문의하거나 Adobe 지원 `marketocares@marketo.com`에 문의하십시오.

* Marketo Engage 구독을 마이그레이션할 Adobe Admin Console(또는 Adobe 조직)를 확인합니다. Marketo Engage의 기본 대화 자동화 도구인 [Dynamic Chat](/help/dynamic-chat/dynamic-chat-overview.md){target="_blank"}용 Adobe Admin Console이 있을 수 있습니다. Marketo Engage 구독은 Dynamic Chat과 동일한 조직에 배포되어야 합니다.

* IT 팀과 함께 [이 맨 위에 나열된 모든 Adobe 도메인을 Marketo Engage](https://experienceleague.adobe.com/ko/docs/marketo/using/getting-started/initial-setup/configure-protocols-for-marketo){target="_blank"}하여 Adobe ID로 마이그레이션 후 허용 목록에 추가하다 액세스가 중단되는 것을 방지합니다.

* **선택 사항:** [사용자 마이그레이션 전에 SSO(Single Sign-On) 구현](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/understanding-marketo-subscription-and-user-migration-to-the-adobe-admin-console#subscription-migration-complete){target="_blank"}.

  >[!NOTE]
  >
  >Marketo Engage 지원 SSO와 Adobe Admin Console SSO 사이에는 차이가 있습니다. 따라서 구성을 변경해야 할 수 있습니다.

* **선택 사항:** Marketo Engage 사용자가 인증된 상태를 유지할 수 있도록 사용자 마이그레이션 전에 [원하는 최대 세션 수명을 사용자 지정](https://helpx.adobe.com/kr/enterprise/using/authentication-settings.html#advanced-settings){target="_blank"}합니다.

* [샘플 전자 메일 섹션](#announce-the-migration-timeline)에서 시스템 관리자와 통신하는 방법을 알아봅니다.

### 2. Adobe ID로 마이그레이션하는 경우의 변경 사항과 영향에 대해 숙지하십시오 {#familiarize-yourself-with-the-changes}

아래 비디오에서는 Marketo Engage 제품 관리 팀이 마이그레이션 여정과 예상 내용을 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3432371/?t=170/?quality=12&learn=on&captions=kor){transcript=true}

Marketo Engage 관리자를 위한 이 항목에 대한 자세한 내용은 다음 도움말 문서에서 확인할 수 있습니다.

* [사용자 설정 검사 목록](https://experienceleague.adobe.com/ko/docs/marketo/using/getting-started/initial-setup/user-setup){target="_blank"}

* [Adobe Identity Management 개요](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/adobe-identity-management-overview){target="_blank"}

* [Marketo 구독 및 Adobe Admin Console으로의 사용자 마이그레이션 이해](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/understanding-marketo-subscription-and-user-migration-to-the-adobe-admin-console){target="_blank"}

* [마이그레이션 콘솔을 사용하여 Adobe ID로 마이그레이션](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/migrating-to-adobe-identity){target="_blank"}

* [Adobe Admin Console 사용 방법 이해](https://helpx.adobe.com/kr/enterprise/using/admin-console.html){target="_blank"}

### 3. 내부 팀에 필요한 마이그레이션 타임라인 및 준비 상황을 알려줍니다 {#announce-the-migration-timeline}

* 예약되면 Marketo Engage 관리자 및 사용자 달력에 마이그레이션 날짜를 표시합니다.

   * 내부 타임라인에 맞게 **관리자** > **마이그레이션 콘솔** > **사전 마이그레이션**&#x200B;에서 마이그레이션 날짜를 수정할 수 있습니다. 일정 조정 및 [마이그레이션 날짜 수정](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/migrating-to-adobe-identity#pre-migration){target="_blank"}의 제한 사항에 대해 자세히 알아보세요.

* **시스템 관리자에게 전자 메일 보내기**

다음은 관리자에게 보낼 샘플 이메일입니다. 일반적으로 IT 부서에서 모든 Adobe 라이선스를 관리합니다.

+++ 시스템 관리자에게 보낼 샘플 이메일

**제목: 지원 필요—Marketo Engage 구독을 Adobe Admin Console으로 마이그레이션**

`[IT Administrator/NAME]`님,

Marketo Engage 구독이 곧 Adobe Identity Management 시스템으로 마이그레이션됩니다. `[Marketing Operation team]`은(는) Marketo Engage 사용자에게 미치는 영향을 최소화하기 위해 사용자 마이그레이션이 시작되기 전에 몇 가지 필요한 단계를 완료하는 데 도움이 필요합니다.

`1.` 조직에서 이미 Adobe Admin Console의 다른 Adobe 제품을 관리하는지, Marketo Engage이 동일한 콘솔로 마이그레이션되는지 확인합니다.

* Marketo Engage 구독은 Marketo Engage과 통합된 기본 대화 자동화 도구인 Dynamic Chat과 동일한 조직에 있어야 합니다.

* Admin Console에 대한 질문이나 우려 사항이 있는 경우 `marketocares@marketo.com` 및 CC로 Adobe 지원 센터에 문의하십시오.

`2.` 제목란 &quot;Adobe Marketo Engage `[Package Tier]`에 대한 사용자 액세스를 관리하는 데 필요한 작업&quot;을 사용하여 Adobe에서 전자 메일을 확인합니다. 이 이메일은 Marketo Engage 라이선스가 Admin Console에서 프로비저닝된 후 전송되었습니다. 시스템 관리자만 이 이메일을 수신하게 됩니다. 수령하시면 즉시 알려주시기 바랍니다.

* Adobe은 사용자를 조직의 기존 콘솔로 자동으로 마이그레이션하기 위해 Admin Console 시스템 관리자인 사용자의 동의를 구할 수 있습니다. 제목란 &quot;Adobe Marketo Engage `[Package Tier]`에 대한 사용자 액세스를 관리하는 데 필요한 작업&quot;이 있는 이메일에서 &quot;시작하기&quot; 버튼을 클릭하여 동의 페이지로 이동합니다.

`3.` 마이그레이션 후 Marketo Engage이 experience.adobe.com에서 Adobe Experience Cloud으로 제공됩니다. Marketo Engage 액세스가 중단되지 않도록 [이(가) 위에 나열된 모든 Adobe 도메인을 문서 허용 목록](https://experienceleague.adobe.com/ko/docs/marketo/using/getting-started/initial-setup/configure-protocols-for-marketo){target="_blank"}하십시오.

`4.` **선택 사항:** Adobe Admin Console에서 SSO(Single Sign-On)를 설정합니다.

* 앞으로 Adobe ID에서 SSO로 로그인하는 사용자에게 이점을 제공하려면 사용자 마이그레이션이 발생하기 전에 Adobe Admin Console에서 SSO 설정을 지원하십시오.

`5.` **선택 사항:** Adobe Admin Console에서 더 긴 [최대 세션 수명](https://helpx.adobe.com/kr/enterprise/using/authentication-settings.html#advanced-settings){target="_blank"}을 설정합니다.

* 사용자가 자주 로그인하지 않도록 하려면 고급 설정에서 세션 수명을 더 긴 기간으로 사용자 지정하세요.

전환기에 협조해 주셔서 감사합니다. 마이그레이션을 진행할 수 있도록 이 단계를 완료하면 알려주십시오.

감사합니다.

`[Your Name]`

+++

* **Marketo Engage 사용자에게 전자 메일 보내기**

다음은 관리자 권한이 **없는** Marketo Engage 사용자를 위한 샘플 전자 메일입니다.

+++ 예정된 마이그레이션을 알리는 샘플 이메일

**제목: 중요 업데이트—Marketo Engage 구독을 Adobe Admin Console으로 마이그레이션**

Marketo Engage 사용자님께,

Marketo Engage 인스턴스 및 로그인 방법에 관한 중요한 발표가 있습니다. Adobe은 Marketo Engage 구독과 사용자를 Adobe Admin Console으로 이전하여 한 곳에서 모든 제품 관리를 중앙 집중화할 수 있도록 하고 있습니다. 마케팅 워크플로우, 콘텐츠, 통합 또는 자산에는 영향을 주지 않습니다.

**키 세부 정보:**

* **마이그레이션 날짜**: `[Specify the scheduled date - please find this in Marketo Engage under Admin > Migration Console > Pre-migration]`

* **시간**: 구독에 대한 마이그레이션이 현지 시간으로 자정 즈음에 시작됩니다.

* **영향**: 사용자 마이그레이션 중에 제품 액세스 손실이 없습니다. 계정이 마이그레이션 중일 때 로그인하면 로그아웃되고 마이그레이션 후 Adobe ID를 사용하여 몇 분 안에 다시 로그인하라는 메시지가 표시됩니다.

* **이점**: Adobe ID 또는 Adobe Federated ID(SSO)를 통해 단일 Adobe ID를 사용하여 Marketo Engage 및 기타 Adobe 제품을 인증합니다.

**수행할 작업:**

`1.` **준비**: Adobe ID로 마이그레이션하려면 전자 메일 확인이 필요합니다.

i. 링크가 포함된 이메일 확인 요청 이메일을 받았습니다(3일 동안 유효). 링크가 만료된 경우 &quot;내 프로필&quot; 아이콘을 클릭하여 Marketo Engage 내에서 확인 이메일을 다시 보낸 다음 **내 계정** > **계정 설정** > **확인 다시 보내기**(으)로 이동할 수 있습니다.

아.. 이메일 인증이 성공하려면 활성 사용자 세션이 필요합니다. 먼저 ID 공급자(IdP) URL을 사용하여 Marketo Engage 구독에 로그인하십시오.

`2.` **온보드**: 사용자 계정이 마이그레이션되면 로그인 방법 변경 사항과 관련된 전자 메일을 Adobe에서 받게 됩니다.

i. &#39;초대 수락&#39; 버튼을 클릭하고 Adobe ID를 사용하여 로그인하여 새 초대를 수락합니다.

아.. Adobe 로그인 페이지에서 기존 Adobe ID으로 로그인하십시오.

iii. 탐색하려는 engage-xx.marketo.com 도메인에서 이전에 책갈피가 지정된 URL에 대해 먼저 Marketo Engage 인스턴스에 로그인해야 합니다.

`3.` **연락처**: 계정이 마이그레이션된 후 질문이 있거나 지원이 필요한 경우 또는 계정이 마이그레이션되지 않았으며 Marketo Engage에 대한 액세스 권한이 없는 경우 `[your internal contact email/phone]`의 Marketo Engage 마이그레이션 팀에 문의하세요.

전환기에 협조해 주셔서 감사합니다. 시스템을 안전하게 유지하기 위한 귀사의 이해와 헌신에 감사드립니다.

감사합니다.

`[Your Name]`

+++
