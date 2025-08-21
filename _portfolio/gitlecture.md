---
layout: post
title: FFT & CT
img: "assets/img/0.post/2025-05-02/0.png"
date: 02-05-2025
tags: [Radon Transfrom, FFT, Iine Integral, Computer Algorithm]
---

**source code**<br>
Python 소스코드 파일첨부 | [CT Medical Image](https://wiki.cancerimagingarchive.net/display/Public/TCGA-LUAD) <br>
**run**<br>
32.53s

## Radon Transfrom

**과정 요약**<br>

> - 라돈변환은 이미지를 **여러각도로 회전** 시켜야 하는데 **회전 과정에서 이미지가 잘릴 수 도 있다**.
> - 때문에 잘리는것을 방지하기위해 **잘리지 않는 최소크기(대각선)** 만큼 **패딩**을 해준다
> - 원래는 CT가 회전하면서 투영하는 것을 이미지를 회전하면서 투영하는 것으로 구현한다.
> - 회전된 이미지에 대해 **선적분**을 한다.
> - 결과를 sinogram으로 쌓고 반환한다.
> - 여기서 선적분은 실제로 선적분 연산을 하지는 않는다. **이미지가 픽셀로 조밀하기 때문에 수치근사**한다
> - **디지털 이미지**는 연속이 아닌 **discrete**하기 때문에 적분대신 **픽셀 줄 합산**을 한다
> - 실제로도 CT 스캐너도 **무한한 해상도로 선적분하는 것이 아닌 이산데이터**를 받아서 **수치근사**한다

