---
layout: single
title:  "유니티 - Oculus VR Setting"
categories: VR
tag: [Blog, Study, Unity, C#, Tech, VR, Oculus]
toc: true
---

> ## Oculus VR 개발환경 셋팅

> - Meta Quest 공식 홈페이지 문서를 보며 설정해보자

1. Create Unity Project
    1. 프로젝트 생성
    
    ![CreateProject](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/ProjectCreate.png)
    2. 버전선택, 코어선택, 프로젝트이름 설정
    
    ![CreateProject_versionSelect](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/ProjectCreateSetting.png)
    3. 에셋스토어에서 Oculus Integration 다운로드
    
    ![AssetStoreOculus](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/AssetStore.png)
    4. PackageManager 에서 버전선택 및 Import
    
    ![PackageManagerOculus](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/PackageManager.png)

2. Set Target Platform
    1. 프로젝트 메뉴 File -> Build Settings
    2. 플랫폼 안드로이드 변경
       - Oculus Store 또는 App Lab 에 앱을 제출하려면 HMD에 설치하고 출시할수있는 패키지를 만들어야하는데, 파일 확장자 APK
    
    ![SetTargetPlatform](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/SetTargetPlatform.png)

3. General Settings
   1. 프로젝트 메뉴 Edit -> Project Settings -> Player
   2. Company Name, Product Name, Version 설정

    ![GeneralSettings](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/GeneralSettings.png)

4. Package Identification Settings
   1. 프로젝트 메뉴 Edit -> Project Settings -> Player 에서 Other Settings 탭을 확장
   2. Other Settings 탭에서 Identification
   3. Package Name 설정 : `com.CompanyName.AppName`
   4. Minimum API Level 변경 : Oculus에서의 최소 Android 버전은 Android 10(API level 29) 이다

    ![PackageIdentification](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/PackageIdentificationSettings1.png)

5. Configuration Settings
   1. 프로젝트 메뉴 Edit -> Project Settings -> Player
   2. Other Settings 탭에서 Configuration
   3. Scripting Backend 를 IL2CPP 로 변경
   4. Targer Architectures 에서 ARMv7 선택 해제 후 ARM64 선택 체크 : Meta Store 에서는 64비트 앱만 허용된다
   5. Install Location 은 자동으로 선택

    ![ConfigurationSettings](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/ConfigurationSettings.png)

6. XR Management
   1. Package Manager에서 Oculus XR Plugin 다운로드 및 설치

    ![PakageManagerXROculus2](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/XRPlugin3.png)

   2. 메뉴 Edit -> Project Settings -> XR Plug-in Management
   3. XR Plugin Management 설치

    ![PakageManagerXROculus2](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/XRPlugin.png)

   4. Android 탭에서 Oculus 선택

    ![PakageManagerXROculus3](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/XRPlugin2.png)


7. Rendering Settings
   1. 메뉴 Edit -> Project Settings -> Player -> Other Settings 에서 Rendering
   2. Color Space 를 Linear 로 변경
   3. Auto Graphics API 체크 해제
   4. Graphics APIs Vulkan 삭제 OpenGLE3 을 권장
   5. Multithreaded Rendering 체크

    ![RenderingSetting](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/RenderingSettings.png)

> ## 셋팅이 작 적용되었는지 확인

1. Scene 생성 후 Main Camera 제거
2. OVRCameraRig 프리팹을 Hierarchy 창에 끌어다 놓는다
3. Oculus 와 연결 후 Scene 실행

![UnityScene](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/SceneSetting.png)

![PlayVideo](https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-12-15-VR-OculusSetting_posting/UnityScenePlayWithOculus.mp4)
