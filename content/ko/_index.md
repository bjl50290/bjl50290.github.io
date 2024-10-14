---
# Leave the homepage title empty to use the site title
title: 백정렬
date: 2024-10-01
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: Biography
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin

  - block: experience
    content:
      items:
        - title: 주식회사 디프리
          date_start: '2024-01-01'
          description: |
            소프트웨어 엔지니어

        - title: 주식회사 하이컨시
          date_start: '2020-01-01'
          date_end: '2021-03-01'
          description: |
            저작권팀

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
