---
title: Adobe Identity Management로 마이그레이션
description: 이 튜토리얼은 Marketo Engage 구독 및 사용자를 Adobe Admin Console로 마이그레이션하는 과정을 안내합니다.
role: Admin
level: Intermediate, Experienced
recommendations: noDisplay, noCatalog
last-substantial-update: 2024-07-26T00:00:00Z
feature: Marketing
exl-id: 8368a148-c0c8-462f-b166-9efc412c4a0f
source-git-commit: dcfffa299cbcfef489f5b618fae29f745b878d26
workflow-type: ht
source-wordcount: '1250'
ht-degree: 100%

---

# Adobe Identity Management로 마이그레이션

Adobe는 Adobe Marketo Engage 구독 및 사용자를 관리하는 방식을 개선하고 있습니다. Marketo Engage 구독 및 사용자를 Adobe Admin Console로 마이그레이션하여 조직의 생산성을 높이고자 합니다.

이 튜토리얼은 마이그레이션 과정을 안내하여 사용자가 중앙 위치에서 다른 Adobe 계정 및 제품과 함께 Adobe Marketo Engage를 관리할 수 있도록 돕습니다. 마이그레이션은 필수 사항이며 마케팅 워크플로, 콘텐츠, 통합 또는 자산에는 영향을 미치지 않습니다.

## Marketo Engage 관리자를 위한 마이그레이션 전 체크리스트 {#pre-migration-checklist-for-marketo-engage-administrators}

조직이 Adobe Marketo Engage를 Adobe Admin Console로 마이그레이션할 수 있도록 다음 체크리스트에 따라 향후 변경 사항을 관리하는 것이 좋습니다.

### &#x200B;1. 시스템 관리자 및 IT 팀을 식별하고 필요한 조치에 대해 논의합니다. {#identify-your-system-administrators}

* 조직 내 시스템 관리자가 누구인지 확실하지 않은 경우 Adobe 계정 팀에 문의하거나 Adobe 지원팀(`marketocares@marketo.com`)에 문의하십시오.

* Marketo Engage 구독을 마이그레이션할 Adobe Admin Console(또는 Adobe 조직)을 확인합니다. Marketo Engage의 기본 대화 자동화 도구인 [Dynamic Chat](/help/dynamic-chat/dynamic-chat-overview.md){target="_blank"}을 위한 Adobe Admin Console이 이미 있을 수 있습니다. Marketo Engage 구독은 Dynamic Chat과 동일한 조직에 배포되어야 합니다.

* IT 팀과 협력하여 [이 문서 상단](https://experienceleague.adobe.com/ko/docs/marketo/using/getting-started/initial-setup/configure-protocols-for-marketo){target="_blank"}에 나열된 모든 Adobe 도메인을 허용 목록에 추가하여 Adobe Identity로 마이그레이션한 후 Marketo Engage 액세스에 지장이 없도록 합니다.

* **선택 사항:** 사용자 마이그레이션 전에 [SSO(Single Sign On)를 구현](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/understanding-marketo-subscription-and-user-migration-to-the-adobe-admin-console#subscription-migration-complete){target="_blank"}합니다.

  >[!NOTE]
  >
  >Marketo Engage에서 지원하는 SSO와 Adobe Admin Console SSO 사이에는 차이점이 있습니다. 따라서 구성에 대한 변경을 구현할 필요가 있습니다.

* **선택 사항:** 사용자 마이그레이션 전에 [원하는 최대 세션 수명](https://helpx.adobe.com/kr/enterprise/using/authentication-settings.html#advanced-settings){target="_blank"}을 사용자 정의하여 Marketo Engage 사용자가 인증된 상태를 유지하도록 합니다.

* [샘플 이메일 섹션](#announce-the-migration-timeline)에서 시스템 관리자와 소통해야 할 내용을 확인합니다.

### &#x200B;2. Adobe Identity로의 마이그레이션에 따른 변경 사항 및 영향에 대해 숙지하십시오. {#familiarize-yourself-with-the-changes}

아래 비디오에서 Marketo Engage 제품 관리 팀이 마이그레이션 여정과 예상되는 사항을 안내합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3432371/?captions=kor&t=170/?quality=12&learn=on){transcript=true}

Marketo Engage 관리자를 위한 이 주제에 대한 자세한 내용은 다음 도움말 문서에서 확인할 수 있습니다.

* [사용자 설정 체크리스트](https://experienceleague.adobe.com/ko/docs/marketo/using/getting-started/initial-setup/user-setup){target="_blank"}

* [Adobe Identity Management 개요](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/adobe-identity-management-overview){target="_blank"}

* [Marketo 구독 및 Adobe Admin Console로의 사용자 마이그레이션 이해](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/understanding-marketo-subscription-and-user-migration-to-the-adobe-admin-console){target="_blank"}

* [Migration Console을 사용하여 Adobe Identity로 마이그레이션](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/migrating-to-adobe-identity){target="_blank"}

* [Adobe Admin Console 사용 방법 이해](https://helpx.adobe.com/kr/enterprise/using/admin-console.html){target="_blank"}

### &#x200B;3. 마이그레이션 일정과 필요한 준비 사항을 내부 팀에 알립니다. {#announce-the-migration-timeline}

* 일정이 잡히면 Marketo Engage 관리자 및 사용자의 캘린더에 마이그레이션 날짜를 표시합니다.

   * **관리자** > **Migration Console** > **사전 마이그레이션**&#x200B;에서 내부 타임라인에 맞춰 마이그레이션 날짜를 수정할 수 있습니다. [마이그레이션 날짜 일정 변경 및 수정](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/marketo-with-adobe-identity/subscription-and-user-migration/migrating-to-adobe-identity#pre-migration){target="_blank"} 제한 사항에 대해 자세히 알아봅니다.

* **시스템 관리자에게 이메일 보내기**

다음은 관리자에게 보낼 샘플 이메일입니다. 일반적으로 IT 부서에서 모든 Adobe 라이선스를 관리합니다.

+++ 시스템 관리자에게 보낼 샘플 이메일

**제목: 지원 요청—Marketo Engage 구독을 Adobe Admin Console으로 마이그레이션**

`[IT Administrator/NAME]` 님, 안녕하세요.

Marketo Engage 구독이 곧 Adobe Identity Management 시스템으로 마이그레이션될 예정입니다. `[Marketing Operation team]`은 Marketo Engage 사용자에 대한 영향을 최소화하기 위해 사용자 마이그레이션이 시작되기 전 필수 단계를 완료하는 데 귀하의 도움이 필요합니다.

`1.` 조직에서 이미 Adobe Admin Console의 다른 Adobe 제품을 관리하고 있는지, Marketo Engage가 동일한 콘솔로 마이그레이션되는지 확인해 주십시오.

* Marketo Engage 구독은 Marketo Engage와 통합된 기본 대화 자동화 도구인 Dynamic Chat과 동일한 조직에 있어야 합니다.

* Admin Console과 관련하여 질문이나 우려 사항이 있는 경우 Adobe 지원팀을 참조(CC)하여 `marketocares@marketo.com`으로 문의하십시오.

`2.` Adobe로부터 “Adobe Marketo Engage `[Package Tier]`에 대한 사용자 액세스 관리를 위해 필요한 조치”라는 제목의 이메일이 오는지 확인해 주십시오. 이 이메일은 당사 Admin Console에 Marketo Engage 라이선스가 프로비저닝된 후 발송되었습니다. 시스템 관리자만 이 이메일을 수신하게 됩니다. 이메일을 받으시면 즉시 알려주시기 바랍니다.

* Adobe는 Admin Console의 시스템 관리자에게 사용자를 조직의 기존 콘솔로 자동 마이그레이션하는 것에 대한 동의를 요청할 수 있습니다. “Adobe Marketo Engage `[Package Tier]`에 대한 사용자 액세스 관리를 위해 필요한 조치”라는 제목의 이메일에서 [시작하기] 버튼을 클릭하여 동의 페이지로 이동하십시오.

`3.` 마이그레이션 후 Marketo Engage는 experience.adobe.com에서 Adobe Experience Cloud로 서비스가 제공됩니다. Marketo Engage 액세스 중단을 방지하기 위해 [이 문서 상단](https://experienceleague.adobe.com/ko/docs/marketo/using/getting-started/initial-setup/configure-protocols-for-marketo){target="_blank"}에 나열된 모든 Adobe 도메인을 허용 목록에 추가해 주십시오.

`4.` **선택 사항:** Adobe Admin Console에서 SSO(Single Sign On)를 설정합니다.

* 향후 Adobe Identity에서 SSO로 로그인하는 사용자들에게 편의를 제공하기 위해 사용자 마이그레이션이 발생하기 전에 Adobe Admin Console에서 SSO 설정을 지원하십시오.

`5.` **선택 사항:** Adobe Admin Console에서 [최대 세션 수명](https://helpx.adobe.com/kr/enterprise/using/authentication-settings.html#advanced-settings){target="_blank"}을 더 길게 설정하십시오.

* 사용자가 자주 로그인해야 하는 번거로움을 방지하기 위해 고급 설정에서 세션 수명을 더 긴 기간으로 사용자 정의해 주십시오.

이번 전환 과정에서 협조해 주셔서 감사합니다. 마이그레이션을 진행할 수 있도록 이 단계가 완료되면 알려 주십시오.

감사합니다.

`[Your Name]`

+++

* **Marketo Engage 사용자에게 이메일 보내기**

다음은 관리자 권한이 **없는** Marketo Engage 사용자를 위한 샘플 이메일입니다.

+++ 예정된 마이그레이션을 알리는 샘플 이메일

**제목: 중요 업데이트—Marketo Engage 구독을 Adobe Admin Console으로 마이그레이션**

Marketo Engage 사용자 여러분께,

Marketo Engage 인스턴스 및 로그인 방식에 관한 중요한 공지 사항이 있습니다. Adobe는 모든 제품 관리를 한 곳에서 중앙 집중화할 수 있도록 Marketo Engage 구독 및 사용자를 Adobe Admin Console로 이동하고 있습니다. 이는 마케팅 워크플로, 콘텐츠, 통합 또는 자산에 영향을 미치지 않습니다.

**주요 세부 정보:**

* **마이그레이션 일자**: `[Specify the scheduled date - please find this in Marketo Engage under Admin > Migration Console > Pre-migration]`

* **시간**: 구독에 대한 마이그레이션이 현지 시간으로 자정 무렵에 시작됩니다.

* **영향**: 사용자 마이그레이션 중에 제품 액세스 손실은 없습니다. 계정이 마이그레이션될 때 로그인 상태인 경우 로그아웃되며 마이그레이션 후 몇 분 이내에 Adobe Identity를 사용하여 다시 로그인하라는 메시지가 표시됩니다.

* **이점**: 단일 Adobe Identity(Adobe ID 또는 Adobe Federated ID(SSO))를 사용하여 Marketo Engage 및 기타 Adobe 제품을 인증할 수 있습니다.

**조치 사항:**

`1.` **준비**: Adobe Identity로 마이그레이션하려면 이메일 인증이 필요합니다.

i. 링크가 포함된 이메일 인증 요청 이메일을 받으셨을 것입니다(3일 동안 유효). 링크가 만료된 경우 Marketo Engage 내에서 [내 프로필] 아이콘을 클릭한 다음 **내 계정** > **계정 설정** > **인증 메일 재전송**&#x200B;으로 이동하여 인증 이메일을 다시 전송할 수 있습니다.

ii. 이메일 인증을 성공적으로 마치려면 활성 사용자 세션이 필요합니다. 먼저 ID 공급자(IdP) URL을 사용하여 Marketo Engage 구독에 로그인하십시오.

`2.` **온보딩**: 사용자 계정이 마이그레이션되면 로그인 방법 변경에 관한 이메일을 Adobe로부터 받게 됩니다.

i. [초대 수락] 버튼을 클릭하고 Adobe ID를 사용하여 로그인하여 새 초대를 수락합니다.

ii. Adobe 로그인 페이지에서 기존 Adobe ID로 로그인하십시오.

iii. 이동하려는 engage-xx.marketo.com 도메인에서 이전에 북마크된 URL의 경우 먼저 Marketo Engage 인스턴스에 로그인해야 합니다.

`3.` **문의**: 계정이 마이그레이션된 후 질문이 있거나 지원이 필요한 경우, 또는 계정이 마이그레이션되지 않아 Marketo Engage에 대한 액세스 권한을 잃은 경우 Marketo Engage 마이그레이션 팀(`[your internal contact email/phone]`)에 문의하십시오.

이번 전환 과정에서 협조해 주셔서 감사합니다. 시스템 보안을 유지하기 위한 귀하의 이해와 헌신에 감사드립니다.

감사합니다.

`[Your Name]`

+++
