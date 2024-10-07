---
title: Contact
date: 2022-10-24

type: landing

sections:
  - block: contact
    content:
      title: 저와 놀고 싶다면
      email: bjl5029@gmail.com
      phone: 010-8784-2119
      address:
        street: 동부로10번길 55
        city: 대전광역시
        postcode: '34675'
        country: 대한민국
        country_code: KO
      coordinates:
        latitude: '36.3168'
        longitude: '127.4582'
      directions:
    
      # Automatically link email and phone or display as text?
      autolink: true
    
      # Email form provider
      form:
        provider: netlify
        formspree:
          id:
        netlify:
          # Enable CAPTCHA challenge to reduce spam?
          captcha: false
    design:
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: contact.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen
---
