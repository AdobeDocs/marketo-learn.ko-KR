---
title: 자습서 - REST API 및 토큰을 사용하여 Marketo Engage에서 스마트 캠페인을 트리거하는 방법
description: REST API를 사용하여 Marketo Engage에서 스마트 캠페인을 트리거하고, 내 토큰을 사용하여 이메일을 개인화하는 방법을 알아봅니다.
feature: REST API
role: Admin, Developer
level: Experienced
exl-id: 46e54729-92ab-4bbb-9877-f762708def67
source-git-commit: 99058de9712fbebd631215ef15a6df349ca4c3cc
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# REST API 및 토큰을 사용하여 Marketo Engage에서 스마트 캠페인을 트리거하는 방법

이 튜토리얼에서는 REST API를 사용하여 Marketo Engage에서 스마트 캠페인을 트리거하고 내 토큰을 사용하여 이메일을 개인화하는 방법을 안내합니다. 이 사용 사례는 웨비나 미리 알림, 온보딩 단계 또는 구매 후 후속 조치와 같이 고객이 트리거하는 알림에 이상적입니다.

## 사용 사례 {#use-case}

사용자는 외부 플랫폼(예: 사용자 정의 앱, Pendo, Eventbrite)을 통해 웨비나를 등록합니다. 다음을 자동으로 수행합니다.

* Marketo Engage에서 미리 알림 이메일 트리거
* 다음을 통해 개인화:
   * 사용자의 이름
   * 웨비나 제목
   * 고유한 조인 링크

이 작업은 REST API 및 내 토큰을 사용하여 수행할 수 있습니다.

## 1단계: 스마트 캠페인 만들기 {#step-one}

1. **마케팅 활동**(으)로 이동한 다음 [프로그램](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/core-marketo-concepts/programs/creating-programs/understanding-programs){target="_blank"} 폴더 아래에서 [이라는 새 ](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/core-marketo-concepts/smart-campaigns/understanding-smart-campaigns){target="_blank"}스마트 캠페인`Send Webinar Reminder`을(를) 만듭니다.

1. **스마트 목록** 탭에서 API를 통해 캠페인을 호출할 수 있도록 [트리거를 추가](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/core-marketo-concepts/smart-campaigns/creating-a-smart-campaign/define-smart-list-for-smart-campaign-trigger){target="_blank"}합니다.

   * 트리거로 **캠페인이 요청됨** 선택
   * **Source**&#x200B;을(를) `Web Service API`(으)로 설정

![스마트 목록 트리거 설정](assets/trigger-smart-campaign-rest-api-1.png)

## 2단계: 이메일 콘텐츠 정의 {#step-two}

사용자와 [내 토큰](https://experienceleague.adobe.com/ko/docs/marketo-developer/marketo/rest/assets/emails){target="_blank"}을 모두 참조하는 [전자 메일 자산](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/core-marketo-concepts/programs/tokens/managing-my-tokens){target="_blank"}을 만들거나 편집하세요.

>[!NOTE]
>
>아래 표시된 대로 토큰을 이메일 콘텐츠에 직접 삽입해야 합니다.

```html
Hi {{lead.First Name:default=Customer}}

You're registered for **{{my.WebinarTitle}}**.

Join here: {{my.JoinLink}}
```

토큰을 사용하여 이미지 URL(예: `{{my.WebinarImage}}`)을 동적으로 삽입하는 경우, 토큰을 HTML 이미지 태그에 래핑해야 합니다.

```html
<img src="{{my.WebinarImage}}" alt="Webinar banner" />
```

>[!IMPORTANT]
>
>토큰이 올바른 이미지 태그 내에 없으면 Marketo Enagage **은(는) 이미지를 렌더링하지 않습니다**.

![토큰 사용량을 표시하는 전자 메일 편집기](assets/trigger-smart-campaign-rest-api-2.png)

## 3단계: 프로그램에 토큰 추가 {#step-three}

API를 통해 값을 동적으로 전달하려면 토큰이 Marketo Engage에 이미 존재해야 합니다. 프로그램의 **내 토큰** 탭에서 만들어야 합니다.

1. 상위 프로그램의 **내 토큰** 탭으로 이동합니다.

2. 오른쪽 패널에서 각 동적 값에 대해 **텍스트 토큰**&#x200B;을(를) 드래그합니다.

* `{{my.WebinarTitle}}` - 텍스트 토큰
* `{{my.JoinLink}}` - 텍스트 토큰
* `{{my.WebinarImage}}` - 텍스트 토큰(`src` 태그에서 `<img>`(으)로 사용됨)

![Campaign의 내 토큰 탭](assets/trigger-smart-campaign-rest-api-3.png)

## 4단계: 캠페인 자격 규칙 설정 및 캠페인 활성화 {#step-four}

1. [자격 규칙](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/core-marketo-concepts/smart-campaigns/using-smart-campaigns/edit-qualification-rules-in-a-smart-campaign){target="_blank"}을 구성하여 Smart Campaign을 통해 실행할 수 있는 빈도를 제어합니다.

1. 구성이 완료되면 **활성화**&#x200B;를 클릭하여 Smart Campaign이 API 트리거 요청을 수신할 수 있도록 합니다.

![스마트 캠페인 자격 규칙](assets/trigger-smart-campaign-rest-api-4.png)

## 5단계: REST API를 통해 캠페인 트리거 {#step-five}

### 캠페인 ID 찾기 {#find-the-campaign-id}

API를 통해 스마트 캠페인을 트리거하려면 **캠페인 ID**&#x200B;가 필요합니다.

1. 트리거할 스마트 캠페인을 찾아 선택합니다.

1. 브라우저에서 URL을 확인합니다. `https://app-XXX.marketo.com/#/classic/SC`**1234**`A1ZN38`&#x200B;과(와) 같은 모습입니다.

1. `SC` 뒤에 오는 4자리가 캠페인 ID입니다. 위의 예에서 스마트 캠페인 ID는 &#39;1234&#39;입니다.

다음 엔드포인트를 사용합니다.

```
POST /rest/v1/campaigns/{campaignId}/trigger.json
```

예:

```
POST /rest/v1/campaigns/1234/trigger.json
```

### 예제 요청 본문 {#example-request-body}

```json
{
  "input": {
    "leads": [
      {
        "id": 1002200
      }
    ],
    "tokens": [
      {
        "name": "{{my.WebinarTitle}}",
        "value": "Scaling Customer Engagement in 2025"
      },
      {
        "name": "{{my.JoinLink}}",
        "value": "https://webinars.company.com/join/abc123"
      },
      {
        "name": "{{my.WebinarImage}}",
        "value": "https://experienceleague.adobe.com/ko/docs/marketo-learn/tutorials/events/media_1c6f338a518ada11550084c8ab3a6bbf554ff6eac.jpeg"
      }
    ]
  }
}
```

>[!IMPORTANT]
>
>위의 본문 예제의 `1002200`을(를) Marketo Engage 인스턴스의 올바른 개인 ID로 바꾸십시오.

## Authorization {#authorization}

모든 Marketo REST API 요청에는 OAuth 2.0 액세스 토큰이 필요합니다.

액세스 토큰을 검색하려면 다음 엔드포인트를 사용하십시오.

```
GET /identity/oauth/token?grant_type=client_credentials&client_id=XXX&client_secret=YYY
```

액세스 토큰을 받으면 모든 API 요청에 _쿼리 매개 변수_(으)로 포함하십시오.

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## 우수 사례 {#best-practices}

* 테스트 및 QA를 위해 토큰에 대체/기본값 추가
* 개인 필드에는 `{{lead.token}}`을(를) 사용하고 캠페인 범위 동적 값에는 `{{my.token}}`을(를) 사용합니다.
* Marketo Engage은 요청당 최대 100명의 사용자를 지원합니다
* 사람은 스마트 목록 기준을 충족해야 합니다. 그렇지 않으면 자동으로 건너뜁니다.

## 요약 {#summary}

이 접근 방식을 사용하면 API를 통해 외부 플랫폼에서 트리거되는 스마트 캠페인을 사용하여 커뮤니케이션을 개인화할 수 있습니다. 이 기능은 내 토큰을 사용하여 실시간 데이터를 주입하는 동안 웨비나 등록 확인, 온보딩 이메일 및 트랜잭션 알림과 같은 시나리오에 유용합니다.
