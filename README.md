# 이용찬 | Backend · Cloud

서비스를 만들고 운영하면서 생긴 문제를 측정하고 고치는 일을 해왔습니다. 여담의 인프라와 배포·운영을 맡았고, 모찌에서는 검색·채팅·색인 경로를 개선하고 있습니다.

[GitHub](https://github.com/lee-y-ch) · [이메일](mailto:dldydcks1745@gmail.com)

## 프로젝트

### 여담

**2026.08 ~ 현재 · 6인 팀 · Cloud 담당**

휴대폰과 디지털카메라의 여행 사진을 모아 앨범과 지도에 정리하는 서비스입니다. AWS 인프라 설계, Terraform, CI/CD와 운영 관측을 맡았습니다.

- DB 이전 중 실제 여행 요청과 인증 변경을 유지하는 리허설을 설계하고 구현했습니다. Kafka 요청 수락과 Debezium 인증 변환을 나누고, 순서·처리 기록·트랜잭션 인계를 검증했습니다.
- 이전 요청의 조회 비용과 반복 커밋을 분석했습니다. 인덱스·CDC 처리 개선에 이어 묶음 커밋을 적용한 동일 50 RPS 비교에서 DB 처리 완료 p95를 **52.607초 → 18.849초**로 줄였습니다. 이 수치는 스테이징 리허설 결과입니다.
- 테스트를 독립 Runner로 나눠 BE CI 중앙값을 **369초 → 280초**, AI는 **143초 → 117초**로 줄였습니다. 같은 코드·캐시 조건으로 각 3회 비교했고, Runner 사용 시간 합계와 완료 대기 시간을 구분했습니다.

[Cloud 저장소](https://github.com/100-hours-a-week/KTB4-2nd-Cloud) · [DB 이전 기록](https://github.com/100-hours-a-week/KTB4-2nd-Cloud/wiki/Dev-DB-무중단-마이그레이션)

### 모찌

**2026.05 ~ 현재 · 팀 프로젝트 · Backend**

스크린샷·링크·메모를 저장하면 AI가 정리하고, 필요할 때 다시 찾아 주는 iOS 서비스입니다. FastAPI와 PostgreSQL 기반 백엔드에서 검색·채팅·색인 개선을 맡고 있습니다.

- 저장한 기록이 검색에서 빠지는 상황을 재현하고 검색 품질과 색인 상태를 대조했습니다.
- 임베딩 모델과 문서 벡터가 섞이지 않도록 모델별 색인을 분리하고, 전환·복구 절차를 구성했습니다.
- 채팅 응답 지연을 분석하고 외부 모델 호출과 검색 단계의 처리 흐름을 개선했습니다.

[저장소](https://github.com/dku-mochi/mochi)

### LEO PHOTO

**2026.05 ~ 2026.08 · 개인 프로젝트 · Backend / Infra**

사진을 올리고 검색하는 커뮤니티 서비스입니다. Spring Boot 기반 API와 AWS 인프라를 구현했습니다.

- 검색 결과가 없을 때 약 50만 행을 검사하던 경로를 개선했습니다. 같은 조건에서 3회 측정한 p95 중앙값을 **15.16초 → 70.61ms**로 줄였습니다.
- 조회수를 Valkey에 모아 DB에 반영하도록 구성하고, 같은 게시글 20 RPS 조건의 상세 조회 p95를 **30.32ms → 18.76ms**로 줄였습니다.
- 이미지 변환 실패를 SQS DLQ로 격리하고, 알림과 수동 재처리로 복구하는 과정을 검증했습니다.

[백엔드](https://github.com/lee-y-ch/community-backend) · [인프라](https://github.com/lee-y-ch/community-infra)

## 사용한 기술

- Backend: Java, Spring Boot, JPA, QueryDSL, Python, FastAPI
- 데이터와 메시징: MySQL, PostgreSQL, Redis/Valkey, Kafka, Debezium
- 인프라와 운영: AWS, Terraform, Docker, GitHub Actions, Prometheus, Loki, Grafana

## 학력

단국대학교 소프트웨어학과
