---
title: Marketo API 사용 방법 비디오 - 변수에서 액세스 토큰을 설정하는 방법
description: Postman 애플리케이션을 설정하는 방법과 변수를 활용하여 재사용 가능성을 위해 변수에 데이터를 저장하는 방법을 알아봅니다.
feature: REST API
role: Admin, Developer
level: Beginner
doc-type: Technical Video
duration: 772
last-substantial-update: 2024-08-06T00:00:00Z
jira: KT-15548
source-git-commit: 757f21c965161fba774c2c31e02baa75f4691e4d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# API 도움말 - 변수에서 액세스 토큰을 설정하는 방법

Postman 애플리케이션을 설정하고 변수를 활용하여 재사용 가능성을 위해 변수에 데이터를 저장하는 방법에 대해 알아봅니다. 또한 액세스 토큰을 가져오기 위해 첫 번째 Marketo Engage REST API를 호출하는 방법을 알아봅니다.

>[!PREREQUISITES]
>
>이 비디오를 시작하기 전에 AOI 역할이 있는 API 전용 사용자 이름을 만들고 Launchpad 서비스를 만듭니다. 아래 문서의 단계를 따릅니다.
>
>* [API 전용 사용자 역할 만들기](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user-role){target="_blank"}
>
>* [API 전용 사용자 만들기](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user){target="_blank"}
>
>* [REST API에 사용할 사용자 지정 서비스 만들기](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api){target="_blank"}

**이 비디오에 사용된 참조:**

* Marketo 인증 끝점: `{{{}base_url{}}}/identity/oauth/token?grant_type=client_credentials&client_id={{{}client_id{}}}&client_secret={{{}client_secret{}}}`

* 응답 본문에서 access_token을 가져오는 JS 스크립트(스크립트: 탭 아래에 놓임):

`var jsonData = pm.response.json();
pm.environment.set("access_token", jsonData.access_token);`

* [Marketo Engage 개발자 설명서](https://experienceleague.adobe.com/en/docs/marketo-developer/marketo/rest/authentication){target="_blank"}

>[!VIDEO](https://video.tv.adobe.com/v/3429275/?learn=on)
