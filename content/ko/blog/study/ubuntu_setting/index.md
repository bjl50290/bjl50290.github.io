---
title: Ubuntu 개인 세팅값
date: 2023-10-03
authors:
  - admin
tags:
  - Linux/Ubuntu
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'  
---

### c_compile and run

.bashrc에서 추가

```  
c_building() {
    gcc "$1" -o temp_built && ./temp_built && rm temp_built

}
alias build=c_building
```

### 컴파일 또는 실행 에러시에도 무조건 삭제하도록

```  
(gcc "$1" -o temp_built || true) && (./temp_built || true) && rm temp_built
```

### vim setting

.vimrc에서 추가

``` 
set nocompatible
filetype off 

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

Plugin 'scrooloose/syntastic'
Plugin 'VundleVim/Vundle.vim'

Plugin 'tpope/vim-fugitive'

Plugin 'file:///home/gmarik/path/to/plugin'

Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}

call vundle#end()          
filetype plugin indent on  

set number    " 행번호 표시
set ai    " 자동 들여쓰기
set si " 자동 들여쓰기
set cindent    " c 방식의 들여쓰기
set shiftwidth=4    " 자동 공백 채움 시 4칸
set tabstop=4    " tab을 4칸 공백으로
set ignorecase    " 검색 시 대소문자 무시
set hlsearch    " 검색 시 하이라이트
set nocompatible    " 방향키로 캐럿 이동
set fileencodings=utf-8,euc-kr    " 파일 저장 인코딩 : utf-8, euc-kr
set fencs=ucs-bom,utf-8,euc-kr    " 한글 파일은 euc-kr, 유니코드는 유니코드
set bs=indent,eol,start    " backspace 사용가능
set ruler    " 상태 표시줄에 커서 위치 표시
set title    " 제목 표시
set showmatch    " 다른 코딩 프로그램처럼 매칭되는 괄호 보여줌
set wmnu    " tab 을 눌렀을 때 자동완성 가능한 목록
if has ("syntax")
syntax on    " 문법 하이라이트 on
endif
filetype indent on    " 파일 종류에 따른 구문 강조
set mouse=a    " 커서 이동을 마우스로 가능하도록

 

"젯브레인스타일
colorscheme gruvbox
let g:gruvbox_contrast_dark="hard"
set background=dark
``` 
