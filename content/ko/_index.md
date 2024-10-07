---
# Leave the homepage title empty to use the site title
title: 백정렬
date: 2024-10-01
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: ''
      username: admin
    design:
      background:
        image:
          filename: bg.jpg
          size: cover
          position: center
          parallax: true
          overlay: # 이미지 위에 투명도 레이어 적용
            color: '#000000'  # 검정색
            opacity: 0.1     # % 투명도
          height: 70%
      container: # 컨테이너 크기 조절
        width: 70%  # 너비를 70%로 설정
        max-width: 1200px  # 최대 너비를 1200px로 설정
        padding: 20px  # 내부 여백 조정
        margin: 0 auto  # 가운데 정렬
    text_overlay: # 텍스트 오버레이
      align: center
      color: '#ffffff'  # 흰색 텍스트

  - block: experience
    content:
      items:
        - title: 주식회사 디프리
          date_start: '2024-01-01'
          description: |
            주식회사 디프리에서 소프트웨어 엔지니어로 근무하고 있습니다.

        - title: 주식회사 하이컨시
          date_start: '2020-01-01'
          date_end: '2021-03-01'

  - block: features
    id: features
    content:
      title: <span style="font-size:75%">백정렬의 관심사 및 진로</span>
      text: 관심있는 것들을 나열해봤습니다. <br><br><br><br>
      items:
        - name: 인공지능(AI)
          icon: robot
          icon_pack: fas
          description: <span style="font-size:90%">정보 마이닝, 데이터 마이닝, LLM과 같이 우리 사회를 변화시킬 기술에 관심이 많습니다.</span><br><br>
        - name: 정치/법학
          icon: gavel
          icon_pack: fas
          description: <span style="font-size:90%">사회 현상, 정치 현상에 관심이 있습니다.</span><br><br>
        - name: 보안/네트워크
          icon: shield-alt
          icon_pack: fas
          description: <span style="font-size:90%">보안 사고, 침해 대응 등 보안 기술에 관심이 많습니다.</span><br><br>
        - name: 공연
          icon: theater-masks
          icon_pack: fas
          description: <span style="font-size:90%">공연을 보는 것을 좋아합니다.</span><br><br>
        - name: 안정적인 삶
          icon: home
          icon_pack: fas
          description: <span style="font-size:90%">안정적인 삶을 지향합니다.</span><br><br>
        - name: 주식/투자
          icon: chart-line
          icon_pack: fas
          description: <span style="font-size:90%">투자를 통한 자산증식에 관심이 많습니다.</span><br><br>

  - block: collection
    content:
      id: section-1
      title: 진로/관심사
      count: 3
      offset: 0
      order: desc
      filters:
        folders:
          - blog
    design:
      view: compact
      columns: '2'

  - block: collection
    content:
      id: section-1
      title: 진로/관심사
      count: 3
      offset: 0
      order: desc
      filters:
        folders:
          - activity
    design:
      view: compact
      columns: '2'

  - block: collection
    content:
      id: section-1
      title: 취미
      count: 3
      offset: 0
      order: desc
      filters:
        folders:
          - hobbies
    design:
      view: compact
      columns: '2'


  - block: slider
    content:
      slides:

        - title: <span style="font-size:90%">TREC2024 참여</span>
          content: <span style="font-size:90%">이번 여름에 참여한 TREC2024<span style="font-size:90%">
          align: right
          background:
            image:
              filename: trec1.png
              filters:
                brightness: 0.4
            position: center
            color: '#000'
          link:
            icon: graduation-cap
            icon_pack: fas
            text: 게시글
            url: ../activity/lab/trec2024

        - title: <span style="font-size:90%">전북대 대동제</span>
          content: <span style="font-size:90%">잔나비 공연</span>
          align: right
          background:
            image:
              filename: jannabi1.png
              filters:
                brightness: 0.4
            position: left
            color: '#000'
          link:
            icon: graduation-cap
            icon_pack: fas
            text: 영상시청
            url: ../hobbies/concert/jannabi

        - title: <span style="font-size:90%">논문 작성 경험</span>
          content: <span style="font-size:90%">한국 디지털콘텐츠학회 준비</span>
          align: right
          background:
            image:
              filename: paper1.jpg
              filters:
                brightness: 0.4
            position: center
            color: '#000'
          link:
            icon: graduation-cap
            icon_pack: fas
            text: 게시글
            url: ../activity/lab/write_paper

        - title: <span style="font-size:90%">엔비디아 주식</span>
          content: <span style="font-size:90%">엔비디아는 오를 것인가?</span>
          align: right
          background:
            image:
              filename: nvidia1.jpg
              filters:
                brightness: 0.4
            position: center
            color: '#000'
          link:
            icon: graduation-cap
            icon_pack: fas
            text: 게시글
            url: ../blog/life/nvidia

    design:
      slide_height: '350px'
      slide_width: '100%'
      is_fullscreen: false
      loop: true
      interval: 3000
---
