---
layout: single
title:  "유니티 - Post Processing 기본구성"
categories: UnityTech
tag: [Blog, Study, Unity, C#, Tech, PostProcessing]
toc: true
---

> ## Post Processing

* 예시
  
![Non-PostProcessing](https://docs.unity3d.com/uploads/Main/PostProcessing-0.jpg)

<figure >
<figcaption>
Scene with no post-processing (출처 : Unity Documentation)
</figcaption>
</figure>

![PostProcessing](https://docs.unity3d.com/uploads/Main/PostProcessing-1.jpg)

<figure >
<figcaption>
Scene with post-processing (출처 : Unity Documentation)
</figcaption>
</figure>

> ## 랜더링 파이프라인과의 호환성

Unity에서 각 Render Pipeline 마다의 설정과 적용법이 다르다</br>
그 중 현재 사용하는 `URP (Universal Render Pipeline)` 의 경우를 알아보자</br>

기본적으로 `URP` 에는 `Post-Processing` 패키지가 포함되어있다</br>
> URP 는 Post Processing Stack v2 패키지와 호환되지 않습니다

<p align="center">
<img src="https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-11-21-Tech-%20Post-Processing1_posting/Post-Processing%20Package.png?raw=true" width="500">
<p>

> ## 새로운 Scene에서 Post-Processing 구성하기

### 1. 카메라를 선택하고 Post Processing 체크 확인

<p align="center">
<img src="https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/images/post-proc/camera-post-proc-check.png" width="300" >
<p>

### 2. Scene 에 Volum 컴포넌트가 포함된 게임오브젝트 생성
   * Gameobject > Volume > Global Volume 으로 생성가능

<p align="center">
<img src="https://github.com/tehg36/tehg36.github.io/blob/master/images/2022-11-21-Tech-%20Post-Processing1_posting/Create-Volume.png?raw=true" width="300">
<p>


### 3. Global Volume 게임 오브젝트 선택, Volume 컴포넌트에서 profile 속성 우측의 New 버튼 클릭하여 새로운 Profile 생성

<p align="center">
<img src="https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/images/post-proc/volume-new-scene-new-profile.png" width="400">
<p>

### 4. Volume 구성요소에 Volume Overrides 를 추가하여 효과 추가

<p align="center">
<img src="https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/images/post-proc/volume-new-scene-add-override.png" width="350">
<p>

> ## VR용 URP 의 Post-Processing

* VR 에서는 효과로 인해 메스꺼움 또는 방향 감각 상실이 발생할 수 있다 </br>
* VR 용 비네트 효과 또는, VR 용 렌즈 왜곡, 색 수차 및 모션 블러 효과를 피하자 </br>