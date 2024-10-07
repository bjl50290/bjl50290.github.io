---
title: '데이터베이스 팀 프로젝트 : 전북대 주변 가게 추천 서비스'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - 임성혁
  - 조대인
  - 최홍석

date: '2024-06-10T00:00:00Z'
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

abstract: 장재우 교수님의 데이터베이스 수업에서 진행한 프로젝트 과제입니다.

# Summary. An optional shortened abstract.
summary: 데이터베이스 팀 프로젝트 활동

tags: [데이터베이스, SQL, 추천]

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''
url_code: 'https://github.com/highcastle01/path_recom_db_pj'
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

## 데이터베이스 팀 프로젝트 : 전북대 주변 가게 추천 서비스 ##

### 모임은 어디서? 비는 시간은 어디서? ###

모임을 가져야할 때 혹은 시간이 빌 때 가볼만한 전북대 주변 가게들을 추천해주는 서비스를 데이터베이스 팀프로젝트 주제로 선정하였고 개발하였다.
사용자는 처음 자신이 이 서비스를 쓰는 목적을 선택지에 담으면 이제 데이터베이스에 저장된 내용을 불러와서 서비스 해주었다.

### 프론트엔드 ###

NEXT.js를 이용하여 제작하였다.

### 백엔드 ###

Nest.js와 MySQL을 사용하였다.

### 추천 서비스 ###

추천 서비스는 LLM과 같은 것을 사용하지않고, 단순히 SQL문과 조건문을 이용해 제공하였다.