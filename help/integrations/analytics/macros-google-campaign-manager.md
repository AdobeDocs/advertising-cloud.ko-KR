---
title: 추가 [!DNL Analytics for Advertising Cloud] 매크로 [!DNL Google Campaign Manager 360] 광고 태그
description: 추가 이유 및 방법 알아보기 [!DNL Analytics for Advertising Cloud] 매크로 [!DNL Google Campaign Manager 360] 광고 태그
feature: Integration with Adobe Analytics
exl-id: 05084a85-5890-4a82-b3eb-4520f44f9d66
source-git-commit: c7716aa6f953cda7b03bce85dc85842f25d41172
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# 추가 [!DNL Analytics for Advertising Cloud] 매크로 [!DNL Google Campaign Manager 360] 광고 태그

*Advertising Cloud-Adobe Analytics 통합만 있는 광고주*

*Advertising Cloud DSP에만 적용 가능*

에서 광고 태그를 사용하는 경우 [!DNL Google Campaign Manager 360] Advertising Cloud DSP 광고의 경우, 를 사용하여 Advertising Cloud용 Analytics 매개 변수를 랜딩 페이지 URL에 추가합니다. [`%p` 매크로](https://support.google.com/campaignmanager/table/6096962). 매개 변수 레코드 `s_kwcid` 및 `ef_id` 랜딩 페이지 URL에서 쿼리 문자열 매개 변수를 사용하므로 Advertising Cloud에서 Adobe Analytics에 광고에 대한 클릭 데이터를 보낼 수 있습니다.

매크로 사용 [!DNL Campaign Manager 360] 다음 유형의 디스플레이 및 비디오 광고 [!DNL Analytics for Advertising Cloud] 구현:

* **를 사용하는 광고주 [!DNL Adobe] [!DNL Analytics for Advertising Cloud] 웹 사이트에 구현된 JavaScript 코드**: JavaScript 코드가 이미 `s_kwcid` 및 `ef_id` 쿼리 문자열 매개 변수. 그러나 매크로를 사용하면 타사 쿠키가 지원되지 않을 때 클릭 기반 전환을 포함하도록 추적을 확장합니다. 가장 좋은 방법은 다음 섹션에 있는 매크로를 광고 태그에 추가하여 JavaScript 코드를 통해 캡처되지 않은 추가 클릭스루 데이터를 캡처하는 것입니다.

>[!NOTE]
>
>JavaScript 코드는 쿠키를 계속 사용할 수 있는 동안에만 클릭 추적을 위한 솔루션입니다. 쿠키가 중단되면 다음 매크로를 구현해야 합니다.

* **웹 사이트에서 [!DNL Analytics for Advertising Cloud] JavaScript 코드를 대신 [!DNL Analytics] 클릭스루 데이터만 위한 서버측 전달** (뷰스루 데이터 없음): 다음 매크로는 Advertising Cloud을 통해 구매하는 광고에서 시작되는 온사이트 클릭 활동을 보고하는 데 필요합니다.

## 매크로에 추가 [!DNL Google Campaign Manager 360] 광고

내 [!DNL Google Campaign Manager 360]를 추가하고 을(를) 각 디스플레이 및 비디오 광고에 대한 랜딩 페이지 URL에 추가합니다. `%pamo=!;`

여러 가지 방법으로 랜딩 페이지 URL을 지정할 수 있습니다. 각 옵션에 대한 지침은 다음 하위 섹션에 포함되어 있습니다.

다음은 접미사를 사용하여 형식이 지정된 랜딩 페이지 URL의 예입니다.

```
https://www.adobe.com/home?someparam1=somevalue1&%pamo=!;
```

>[!NOTE]
>
>
>* 랜딩 페이지 URL에 일반적이지 않은 해시 기호(#)가 포함된 경우 `amo` 매개 변수 앞에 해시 기호를 추가합니다.
>* 다음에 다른 매개 변수가 포함되지 않는 경우 `amo` 매개 변수를 추가한 다음 그 뒤에 매개 변수(예: &amp;a=b)를 추가합니다. 예:`https://www.adobe.com/home?someparam1=somevalue1&%pamo=!;&a=b#login`


### 광고주 수준 랜딩 페이지 URL 접미사 구성

1. 기본 메뉴에서 [!UICONTROL Advertisers] 탭.
1. 광고주 이름을 클릭합니다.
1. 에서 [!UICONTROL Landing page URL suffix] 설정, 포함 `%pamo!;` 에서 [!UICONTROL URL suffix] 필드.

![advertiser 수준 설정](/help/integrations/assets/macro-ggl360-advertiser.png)

### 캠페인 수준 랜딩 페이지 URL 접미사 구성

1. 기본 메뉴에서 [!UICONTROL Campaigns] 탭.
1. 캠페인 이름을 클릭합니다.
1. 클릭 [!UICONTROL Properties].
1. 에서 [!UICONTROL Landing page URL suffix] 설정, 포함 `%pamo!;` 에서 [!UICONTROL URL suffix] 필드.

![campaign 수준 설정](/help/integrations/assets/macro-ggl360-campaign.png)

### 광고 수준 랜딩 페이지 URL 접미사 구성

1. 기본 메뉴에서 [!UICONTROL Campaigns] 탭.
1. 캠페인 이름을 클릭합니다.
1. 에서 [!UICONTROL Views] 메뉴, 선택 [!UICONTROL Creatives].
1. 크리에이티브 이름을 클릭합니다.
1. 에서 [!UICONTROL Click tags] 설정, 포함 `%pamo!;` 에서 [!UICONTROL Landing page] 클릭 태그의 열.

![크리에이티브 수준 설정](/help/integrations/assets/macro-ggl360-creative.png)

## 방법 [!DNL Analytics for Advertising Cloud] 매크로가 DSP에서 확장됨

DSP에서 다음을 포함하는 광고를 만들 때 [!DNL Analytics for Advertising Cloud] 매개 변수(`amo`), `ef_id` 및 `s_kwcid` 매크로가 클릭 URL에 자동으로 추가됩니다. 가장 좋은 방법은 DSP에서 태그를 확인하여 `ef_id` 및 `s_kwcid` 매크로가 있습니다.

다음은 의 예입니다 [!DNL Google Campaign Manager 360] [ins 태그](https://support.google.com/campaignmanager/answer/6080468) 표시됩니다.

```
<ins class='dcmads' style='display:inline-block;width:160px;height:600px'
data-dcm-placement='N6482.2155306TUBEMOGUL/B23486129.261313631'
data-dcm-rendering-mode='iframe'
data-dcm-https-only
data-dcm-resettable-device-id=''
data-dcm-app-id='' data-dcm-click-tracker='${TM_CLICK_URL}'
data-dcm-param-amo='ef_id=${TM_USER_ID}:${TM_DATETIME}:d&s_kwcid=AC!${TM_AD_ID}!${TM_PLACEMENT_ID}'>
<script src='https://www.googletagservices.com/dcm/dcmads.js'></script>
</ins>
```

사용자가 광고를 클릭하면, [!DNL Google Campaign Manager 360] 보기 횟수 `%pamo` 는 URL 접미사에 있고 `amo` 매개 변수를 URL에 추가합니다.


>[!MORELIKETHIS]
>
>* [개요 [!DNL Analytics for Advertising Cloud]](overview.md)
>* [에서 사용하는 Advertising Cloud ID [!DNL Analytics]](/help/integrations/analytics/ids.md)
>* [추가 [!DNL Analytics for Advertising Cloud] 매크로 [!DNL Flashtalking] 광고 태그](macros-flashtalking.md)

