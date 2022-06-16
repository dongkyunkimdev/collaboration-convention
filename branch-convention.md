
![image](https://user-images.githubusercontent.com/49021557/173761133-fe390ad9-6a0f-458a-8859-f28043a044e5.png)


### Branch Naming
- feature/{issue-name}
- release-1.2
- hotfix-1.2.1

### master(main)
- **제품으로 출시**될 수 있는 브랜치
### develop
- **다음 출시 버전을 개발**하는 브랜치
- `master` 브랜치에서 분기
### feature
- **기능을 개발**하는 브랜치
- `develop` 브랜치에서 분기
- 작업이 완료되면 `develop` 브랜치에 merge하고 브랜치 제거
- feature/{issue name}
### release
- **이번 출시 버전을 준비**하는 브랜치
- 개발 목표가 달성되면 `develop` 브랜치로부터 생성
### hotfix
- **출시 버전에서 발생한 버그를 긴급하게 수정** 하는 브랜치
- `master`, `release` 브랜치에서 분기하고, merge되면 브랜치 제거

Git-flow의 순수성을 지키기에 급급한 것 보단, 상황에 따른 브랜치 전략을 가져가는 것이 좋다고 한다.

## Reference
- [우린 Git-flow를 사용하고 있어요](https://techblog.woowahan.com/2553/)
- [Git 브랜치의 종류 및 사용법](https://gmlwjd9405.github.io/2018/05/11/types-of-git-branch.html)
- [Semantic Versioning](https://semver.org/lang/ko/)