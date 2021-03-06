# UnityProject (미정)
## 프로젝트 개요
```
프로젝트 설명은 프로젝트 완료 후 수정될 수 있습니다.
```

- 본 프로젝트는 KGA의 프로그래밍 교육 기간중에 진행하는 프로젝트이다.

- 창작 또는 모작이 가능한 프로젝트이나 추후 출시 가능한 프로젝트를 목적으로 하여
  
  창작 게임을 선택하였으며 사용되는 리소스는 상업적으로 사용 가능한 라이센스를 활용한다.
  
- 기능 개발을 우선으로 하며 콘텐츠 볼륨은 추후 개발 또는 진행상황에 결정한다.

### 개발 환경
- Unity 2021.3.15f1

### 개발 인원
- 1인

### 프로젝트 기간
- 약 1주일

(프로젝트 기간에 GPGS IAP UnityAds 등 출시버전을 위한 개발 기간은 산정하지 않습니다.)

***

## [(Link) 개발 리스트 정리 시트](https://docs.google.com/spreadsheets/d/1pZK6LebXEwzqyYYv5XKRE6p39oa6tqng-rD58605BSY/edit?usp=sharing)

***

## 게임 소개

### 장르
- Trap Action, Defence

유사게임 레퍼런스
1. [Orcs Must Die!](https://store.steampowered.com/app/1522820/Orcs_Must_Die_3/)
2. [Rock Of Ages](https://store.steampowered.com/app/22230/Rock_of_Ages/)
3. [Dungeon Warfare / 던전 워페어](https://store.steampowered.com/app/355980/Dungeon_Warfare/)
4. [Kagero / 카게로](https://youtu.be/aIsiaGHWLg4?t=599)
5. [unholy heights / 메종 드 마왕](https://store.steampowered.com/app/249330/Unholy_Heights)

### 디자인
- 3D Cartoon graphic

디자인 레퍼런스
1. [궁수의 전설](https://play.google.com/store/apps/details?id=com.habby.archero&hl=ko&gl=US)
2. [마녀의샘](https://play.google.com/store/apps/details?id=com.kiwiwalks.witchspringlunaml)
3. [드래곤 퀘스트 빌더즈](https://namu.wiki/w/%EB%93%9C%EB%9E%98%EA%B3%A4%20%ED%80%98%EC%8A%A4%ED%8A%B8%20%EB%B9%8C%EB%8D%94%EC%A6%88%202:%20%ED%8C%8C%EA%B4%B4%EC%8B%A0%20%EC%8B%9C%EB%8F%84%EC%99%80%20%ED%85%85%20%EB%B9%88%20%EC%84%AC)

### 시스템

#### 타이틀
#### 인게임
- 준비 단계

  몬스터의 등장 위치가 표시된다.

  타일맵에 보유한 금액만큼의 함정을 설치할 수 있다.
  
  함정

    - 공격형
      - n초마다 몬스터에게 일정 데미지를 주는 함정을 발동시킨다. (자동형)
      - n초 간격으로 몬스터에게 지속적인 데미지를 주는 함정을 발동시킨다.
    - 이동 방해형
      - n초마다 몬스터를 특정 방향으로 날려버리는 함정을 발동시킨다. (자동)
      - 이 구간을 지나는 몬스터의 이동속도를 감소시킨다 (자동)
    - 특수형 (추후)
      - 몬스터에게 특정 상태를 부여하는 함정 (자동)
      
        (ex. 기름 : 몬스터에게 기름 상태를 부여한다 -> 화염 트랩의 효과에 반응이 발생하는 등의 효과를 볼 수 있다.)
    - 발동형
      - 플레이어의 조작을 통해 발동시키는 함정 (수동)

        (ex. 돌굴리기 : 특정 방향으로 돌을 굴려 몬스터에게 데미지를 주고 몬스터를 납작하게 만든다.)

  설치한 함정은 함정 슬롯에 등록된다.
  
  함정의 설치가 완료되면 게임시작 버튼을 통해 플레이단계로 넘어간다.

  ```
  핵심 기능
  1. 맵 (몬스터 생성 위치, 타일 구성)
  2. 트랩 (구매, 판매, 슬롯등록)
  3. 재화 (보유 골드, 트랩 비용)
  4. 트랩
    1) 트랩 방향 회전
    2) 트랩 발동 조건 (트리거, 버튼 클릭)
    3) 쿨타임 (n초마다 재사용 가능)
    4) 트랩 기능 (데미지 적용, 이동속도 감소, 몬스터 날리기, 스턴)
    5) 트랩 사용 (발동 트랩)
  ```       

- 플레이 단계
  
  몬스터 등장 위치에 몬스터가 등장한다.
  
  플레이어는 플레이어 캐릭터와 함정을 사용하여 몬스터를 막아야한다.
  
  - 플레이어 캐릭터
  
    - 이동 : 플레이어의 조작을 통해 이동이 가능하다
    - 공격 : 근접 또는 원거리 공격이 가능하다.
    - HP : HP가 0이 되면 캐릭터는 행동불능 상태가 되고 n초 후 리스폰 지점에서 리스폰된다.
    
  - 함정
    
    함정 슬롯의 함정을 클릭하면 액티브 함정을 발동시킬 수 있다.
    
    함정 슬롯에는 함정의 사용 쿨타임이 표시된다. (시계방향 이미지와 시간이 표시된다.)
    
  - 몬스터
    
    - 생성 : 플레이 단계가 시작되면 몬스터 등장 위치에 몬스터가 생성된다.
    - 이동 : 이동 속도만큼 골인 지점으로 이동한다.
    - 공격 : 근처에 플레이어가 있으면 공격력만큼 플레이어를 공격한다 (우선순위 낮음)
    - 사망 : HP가 0이 되면 사망하고 보상을 드랍한다.
    
    몬스터가 골인 지점에 도착하면 최대 자신이 드랍하는 골드만큼 플레이어 골드를 훔쳐간다.
    
    훔쳐가는 몬스터가 쓰러지면 몬스터의 골드 + 훔쳐간 골드를 받을 수 있다.
    
  - 스테이지 종료 조건
  
    맵에 남아있는 몬스터가 없으면 스테이지는 종료된다. (몬스터가 돈을 훔쳐 달아났다던가, 소탕을 완료했다던가)
    
    ```
    핵심 기능
    1. 플레이어 이동 조작
    2. 캐릭터(플레이어, 몬스터) 자동 공격
    3. 플레이어 사망 및 리스폰
    4. 함정 발동
    5. 함정 UI
    6. 몬스터
      1) 특정 지역에 생성
      2) 목표 지점으로 이동
      3) 보상 정보
    7. 스테이지 종료 조건 판단
    ```


(작성중)
