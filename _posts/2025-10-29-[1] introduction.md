---
excerpt: "[1]introduction"
name: J
writer: J
categories: [강의 정리, 세라프 이용법] # [메인 카테고리, 서브 카테고리]
tags:
  - []

toc: true
toc_sticky: true

date: 2025-10-29
last_modified_at: 2024-10-29

# --- 아래 부터 content
---

# The structure of Seraph
![alt text]({{ '/assets/img_20251030/image.png' | relative_url }})
- 3개의 서버 클러스터로 구성
- 1개의 클러스터는...
    - 1개의 master
    - 1개의 NAS storage: 파일 저장
    - 컴퓨팅 노드들
- 접속하려면 IP Address 보고 xxx에 해당 숫자 넣어서 접속

![alt text]({{ '/assets/img_20251030/image-1.png' | relative_url }})

### 용어
![alt text]({{ '/assets/img_20251030/image-2.png' | relative_url }})
- Master 
    - 최초로 접속 되는 곳
    - GPU들을 여기서 배정
    - 여긴 GPU가 없기에 CPU node
- NAS/Storage/File system
    - 작업한 코드들...모델 웨이트들..저장 장소(모든 노드에서 공유해야하기에)
- Computing node / GPU node

# 접속이 뭐냐?

![alt text]({{ '/assets/img_20251030/image-3.png' | relative_url }})

# What is Slurm?
- Slurm: 리소스 매니저 / Scheduler for cluster
    - GPU가 굉장히 많고, 노드들이 흩어져 있기에.. 이들을 하나로 묶어서 유기적으로 써야함.
- 하는 일:
    1. resource(cpus, mems, gpus)들을 자동으로 할당
    2. Queueing: 자리가 없으면 저장..후 자리 나면 보냄

![alt text]({{ '/assets/img_20251030/image-4.png' | relative_url }})
-> job: 딥러닝 연구 하다보면, 모델 train -> test가 일련의 스크립트로 구성! 이걸 job으로 구성<br>
-> job을 master에게 submit. master가 빈 노드에 할당<br>
![alt text]({{ '/assets/img_20251030/image-5.png' | relative_url }})
-> Slurm 없는 경우...유저가 빈노드 수동으로 찾아야함.
![alt text]({{ '/assets/img_20251030/image-6.png' | relative_url }})
-> batch 여러개 던져놓고 퇴근하면.. master가 알아서 해줌.