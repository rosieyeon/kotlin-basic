# Android

- UI 관련 강의 정리

<br>



## General Purpose Language

- 범용적인 목적을 가지고 있는 언어
- kotlin, python, java, c, c++, swift, ...

<br>



## Domain Specific Language(DSL)

- 도메인 특화 언어 → 특수한 목적을 달성하기 위한 언어
- 간단한 문법
- XML

<br>



## XML (eXtensible Markup Language)

- 안드로이드에서 UI를 그리기 위해서 채택한 언어
- Markup Language
  - 태그로 마크를 하여 내용을 작성
  - 태그 → 범위를 정해
  - eXtensible → 확장이 가능. 태그안에 태그가 추가 가능함

<br>



## 단위

- px (pixel)
  - 실제 존재하는 물리적인 단위
  - 같은 단위 면적에 픽셀이 많이 있을수록 해상도가 높다
  - 픽셀은 물리적인 화면을 구성하는 최소 단위
- dp (Density-Independent Pixels)
  - 픽셀 독립 단위
  - 화면의 크기가 달라도 동일한 비율로 보여주기 위해서 안드로이드에서 정의한 단위
  - 비율로 크기를 정한다
- sp (Scale-Independent Pixels)
  - 시스템 설정에 영향을 받는 단위
  - 텍스트 크기를 지정하기 위해서 사용하는 단위
  - 보통 sp가 아닌 dp로 설정을 함
- dpi (Dot Per Inch)
  - 100dpi → 1인치당 픽셀이 100개 들어있다는 뜻
  - ldpi: 120dpi
  - mdpi: 160dpi (기본)
  - hdpi: 240dpi
  - xhdpi: 320dpi

<br>



## View Component

- 위젯 (widget), 뷰 클래스(View class), 컴포넌트(component), 레이아웃(layout)
- 뷰의 종류
  - 부모 뷰, 루트 뷰, 컨테이너 뷰
  - 다른 뷰를 다 가질 수 있는 뷰
  - 자식 뷰
  - 다른 뷰를 가질 수 없는 뷰
  - 부모뷰 → 부모뷰 → 자식뷰 이런식으로 아래로 내려감
- 특수한 뷰
  - 레이아웃 뷰
  - 자식뷰의 배치(위치)를 설정하는 뷰

