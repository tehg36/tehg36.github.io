---
layout: single
title:  "유니티 - XR Interaction Toolkit Setting"
categories: VR
tag: [Study, Unity, C#, Tech, VR, XRInteractionToolkit]
toc: true
---

> ## XR Interaction Toolkit 개발환경 셋팅
    
1. Set Target Platform
    1. 프로젝트 메뉴 File -> Build Settings
    2. 플랫폼 안드로이드 변경
        * 추후 빌드하여 HMD 에서 실행하기 위해

![SetTargetPlatform](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/SetTargetPlatform.png){: align-center}

2. XR Plug-in Setting
    1. Project Settings -> XR Plug-in Management
    2. OpenXR 체크 활성화
        * 안드로이드 탭에서도 같이 활성화해준다

![XRPlugin-Setting1](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRPluginSetting_Window.png){: align-center}

![XRPlugin-Setting2](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRPluginSetting_Android.png){: align-center}

3. XR Plug-in Management -> OpenXR 설정
    1. Interaction Profiles Setting
        * 각 플랫폼 별 필요한 Profile 추가

![OpenXR_Setting1](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRPluginSetting_OpenXR_01.png){: align-center}
    
![OpenXR_Setting2](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRPluginSetting_OpenXR_02.png){: align-center}

4. XR Interaction Toolkit 패키지 임포트
    1. Editor에서 Window -> Package Manager
    2. 좌측상단에 + 버튼 클릭 -> Add package from git URL
    3. `com.unity.xr.interaction.toolkit` 입력 후 Add 버튼 클릭
    4. 기초 다루기 위해 Samples 에서 Starter Assets 임포트

![PackageManager1](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/PackageManager_InteractionToolkit_Install_01.png){: align-center}

![PackageManager2](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/PackageManager_InteractionToolkit_Install_02.png){: align-center}

![PackageManager3](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/PackageManager_InteractionToolkit_Install_03.png){: align-center}

![PackageManager4](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/PackageManager_InteractionToolkit_Install_04.png){: align-center}

> ## Scene을 구성하여 실행해보자

1. Scene 의 MainCamera 삭제 후 Plane GameObject 생성

![DeleteCameraAndCreatePlane](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/DeleteMainCamera_CreatePlane.png){: align-center}

2. Hierarchy 창에서 우클릭 XR -> XR Origin 생성

![CreateXROrigin](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/Create_XROrigin.png){: align-center}

3. XR Origin Setting
    1. 하위 오브젝트 Camera Offset 에 빈 게임오브젝트 두개를 생성
    2. 각각 이름을 Left Hand, Right Hand 로 변경
    3. 각각의 오브젝트에 XR Controller 스크립트 Add
    4. 스크립트 우측상단에 Select Preset 버튼으로 기본 프리셋을 가져와 설정해준다

![XROriginSetting](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XROrigin_CreateHand_Setting.png){: align-center}

![XRControllerSetting1](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRController_TemplateSetting_01.png){: align-center}

![XRControllerSetting2](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRController_TemplateSetting_02.png){: align-center}

![XRControllerSetting3](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XRController_TemplateSetting_03.png){: align-center}

4. Hand Asset을 이용하여 설정
    * Oculus 에서 제공해주는 Hand Asset 사용

    1. Asset Import 하여 생성한 Hand GameObject 하위에 Prefab 넣어준다
    2. 간단한 Material 을 하나 만들어서 Hand Prefab 에 적용

![HandAssetImport](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XROrigin_HandTest_ImportAsset.png){: align-center}

![HandAssetSetMaterial](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XROrigin_HandTest_SetMaterials.png){: align-center}

5. Scene 을 Play 하여 확인
    1. XR Origin 에 Tracking Origin Mode 를 Floor 로 바꿔준다
    2. Add Component 버튼을 눌러 Input Action Manager 스크립트 추가
    3. Action Assets 에 InputAction 설정

![XROrigin1](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XROrigin_Setting_01.png){: align-center}

![XROrigin2](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/XROrigin_Setting_02.png){: align-center}

6. Play!

* 비디오 추가

[PlayVideo](/images/2023-01-11-VR-UnityInteractionToolkitSetting_posting/Play_Scene.mp4)