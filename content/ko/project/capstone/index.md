---
title: '산학실전캡스톤디자인 : 나의 해방일기'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - 임성혁
  - 노형준
  - 진순헌
  - 허완

# Author notes (optional)
# author_notes:
#   - 'Equal contribution'
#   - 'Equal contribution'

date: '2024-09-11T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2024-10-06T00:00:00Z'

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ['paper-conference']

# Publication name and optional abbreviated publication name.
# publication: In *Wowchemy Conference*
# publication_short: In *ICW*

abstract: 컴퓨터인공지능학부의 졸업필수조건이자 누구나 거쳐가야하는 관문. 산학실전캡스톤 활동입니다.

# Summary. An optional shortened abstract.
summary: 전북대학교 컴퓨터인공지능학부 산학실전캡스톤 활동

tags: [캡스톤, 산학실전, 감정일기, AI]

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/capstone-gaon'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
  - example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: example
---

## 캡스톤 ##

### AI 기반 감정일기 ###

졸업을 앞둔 혹은 졸업을 할 생각이 있는 전북대학교 컴퓨터인공지능학부생은 무조건 거쳐야만 하는 것이 바로 캡스톤이다.
이 캡스톤을 4학년도 아닌 3학년에 하게 되면서 꽤나 많은 고민이 되었다.

### 데이터 전처리 ###

Ai hub에서 제공되는 정제된 데이터나 각종 인터넷 커뮤니티의 게시글들을 크롤링한 뒤 가공, 전처리 하였다.

### 프론트엔드 ###

앱으로 개발하기 위해 React Native로 제작 하였다.

### 백엔드 ###

미들웨어를 비롯한 각종 모듈들을 쉽게 다루기 위해 Nest.js를 사용하였고, Postgresql을 사용하였다.

### LLM ###

Kobert 모델을 통해 감정을 분류하고
Llama3 모델을 이용해 메세지를 생성하여 제공하였다.
