---
# Leave the homepage title empty to use the site title
title: Site
date: 2022-10-24
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: ''
      username: Yimseonghyuk
    design:
      background:
        image:
          filename: cover.jpg
          size: cover
          position: center
          parallax: true
          overlay:  
            color: '#000000'  
            opacity: 0.1     
      container:  
        width: 70%  
        max-width: 1200px  
        padding: 20px  
        margin: 0 auto  
    text_overlay:  
      align: center
      color: '#ffffff'  

  - block: slider
    content:
      slides:

      - title: <span style="font-size:90%">Participation in TREC2024</span>
        content: <span style="font-size:90%">TREC2024 I participated in this summer<span style="font-size:90%">
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
          text: Post
          url: ../activity/lab/trec2024

      - title: <span style="font-size:90%">Jeonbuk University Daedong Festival</span>
        content: <span style="font-size:90%">Jannabi Performance</span>
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
          text: Watch Video
          url: ../hobbies/concert/jannabi

      - title: <span style="font-size:90%">Paper Writing Experience</span>
        content: <span style="font-size:90%">Preparing for the Korea Digital Content Association</span>
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
          text: Post
          url: ../activity/lab/write_paper
      
      - title: <span style="font-size:90%">NVIDIA Stocks</span>
        content: <span style="font-size:90%">Will NVIDIA Rise?</span>
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
          text: Post
          url: ../attract/stocks/nvidia

    design:
      slide_height: '350px'
      slide_width: '100%'
      is_fullscreen: false
      loop: true
      interval: 3000

  - block: markdown
    content:
      title: '📚 Introducing Myself!'
      subtitle: ''
      text: |-
        Hello, below are the activities I have been involved in during my university years.
        Although I still have much to learn, I hope you'll enjoy looking through my works and projects.
        Thank you for visiting.
    design:
      columns: '1'

  - block: features
    id: features
    content:
      title: <span style="font-size:75%">Yimseonghyuk's Interests and Career</span>
      text: Here are some of my areas of interest. <br><br><br><br>
      items:
      - name: Artificial Intelligence (AI)
        icon: robot
        icon_pack: fas
        description: <span style="font-size:90%">I am interested in technologies that will change our society, such as information mining, data mining, and LLM.</span><br><br>
      - name: Politics/Law
        icon: gavel
        icon_pack: fas
        description: <span style="font-size:90%">I am interested in social and political phenomena.</span><br><br>
      - name: Security/Networking
        icon: shield-alt
        icon_pack: fas
        description: <span style="font-size:90%">I am interested in security incidents and intrusion response.</span><br><br>
      - name: Concerts
        icon: theater-masks
        icon_pack: fas
        description: <span style="font-size:90%">I enjoy watching performances.</span><br><br>
      - name: Stable Life
        icon: home
        icon_pack: fas
        description: <span style="font-size:90%">I value a stable life.</span><br><br>
      - name: Stocks/Investments
        icon: chart-line
        icon_pack: fas
        description: <span style="font-size:90%">I am interested in wealth building through investments.</span><br><br>
  
  - block: collection
    content:
      id: section-1
      title: Career/Interests
      count: 3
      offset: 0
      order: desc
      filters:
        folders:
          - attract
    design:
      view: compact
      columns: '2'

  - block: experience
    content:
      title: Activities and History
      items:
        - title: President of Coala, Department Club of Computer and AI, Chonbuk National University
          date_start: '2023-12-01'
          description: |
            I am serving as the president of Koala, the department club of Computer and Artificial Intelligence at Chonbuk National University.

        - title: Undergraduate Researcher, Information Mining Lab, Department of Computer and AI, Chonbuk National University
          date_start: '2024-03-02'
          description: |
            I am conducting undergraduate research activities at the Information Mining Lab, Department of Computer and AI, Chonbuk National University.

        - title: Executive Member of JBIG, AI Club at Chonbuk National University
          date_start: '2024-02-01'
          date_end: '2024-08-31'
          description: |
            I served as an executive member of JBIG, the central AI club at Chonbuk National University.

  - block: collection
    content:
      id: section-1
      title: Career/Interests
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
      title: Hobbies
      count: 3
      offset: 0
      order: desc
      filters:
        folders:
          - hobbies
    design:
      view: compact
      columns: '2'

  - block: markdown
    content:
      title: Want to check out my YouTube channel?
      subtitle:
      text: |
        {{% cta cta_link="https://www.youtube.com/@Ganymede3084" cta_text="Welcome to my channel →" %}}
    design:
      columns: '1'
---
