---
title:  "[Python] Progress bar 사용하기"
excerpt: "진행바 사용하기"

categories:
  - DL Code
tags:
  - [python, coding, deeplearning]

toc: True  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. ture 로 해주면 포스트의 목차가 보이게 된다.
toc_sticky: False # true로 해주면 목차가 스크롤을 따라 움직이게 된다!
 
date: 2022-06-15 # 글을 처음 작성한 날짜
last_modified_at: 2022-06-15 # 이 글을 수정한 날짜.
---

## 1. 라이브러리 선언

- argparse 사용을 위해 라이브러리 선언하기

```py
from tqdm.notebook import tqdm
```

## 1. Argparse 코드

```py
pbar = tqdm(range(opt.epochs), unit = 'epoch')
        for epoch in pbar:
            # 본인이 사용하는 코드
            
            pbar.set_postfix({'y_loss' : y_loss, 'd_acc' : d_acc}
```

- for문을 다음과 같이 바꾸면 예쁜 progress bar가 탄생합니다.

- 저는 Domain adaptation 연구를 하고 있어 현재 라벨의 손실값과 도메인의 정확도를 postfix로 놔두었습니다.

  > postfix에 대해 자세한 것은 코드와 아래 사진을 비교하면서 이해하시면 되겠습니다.

- unit에는 자신이 사용하는 단위를 적어주면 됩니다.

- 이에 대한 결과는 다음과 같습니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/104422044/174028786-7b293e2d-8a2e-487a-834e-59853c8be6ff.png" width="800" height="auto">
</p>


- 포스트는 Window10 기준으로 작성되었습니다
