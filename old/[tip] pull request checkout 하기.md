# [tip] pull request checkout 하기(bitbucket)

원격 저장소를 upstream으로 가정한다.( origin 일 경우 origin으로 대체 )

git ls-remote upstream
>
ddcaac7756b0389c6f60281578471fcab3b4a87c        HEAD
ddcaac7756b0389c6f60281578471fcab3b4a87c        refs/heads/develop
93c04fcbd1558ae0250438ac785706970b8c4e3d        refs/heads/feature/specOut
ddcaac7756b0389c6f60281578471fcab3b4a87c        refs/heads/master
20953be6e7d61e76c2bcda301272327ed54e5cf9        refs/pull-requests/1/from  // 이것이 실제 pull-requests 된 브랜치이다.
b1b53f94b3f4999319ca63040f405ef8e4a23509        refs/pull-requests/1/merge
18c1c00c80923507207329914df82c3ad1afa652        refs/tags/realease/v1.0.2
eaf5c7bf837707839d68621ff094fc908c865e02        refs/tags/v1.0.0
c20d0d0e7bb6076471902c266a759a572db3f22d        refs/tags/v1.0.0^{}
fec89d2657b8177585ea38eb23ba94399df33b55        refs/tags/v1.0.3
03490cf5a5dcc4c418099d5b4c932c696ecd949e        refs/tags/v1.0.3^{}
f75a2d61a274188f8b335e5546242622fdccea70        refs/tags/v1.0.4
8989b3b0b3d55759cca31f7e5dfcd33332c10e71        refs/tags/v1.0.6
git pull origin pull/pull-requests/1/from:pr-1 로 할 수도 있지만,

vim .git/config 하면

[remote "upstream"]
url = https://bitbucket.yanolja.in/scm/pf/global-admin-ui.git
fetch = +refs/heads/*:refs/remotes/upstream/*
을 볼 수 있다.

한 라인 더 추가하여

fetch = +refs/pull-requests/*/from:refs/remotes/pr/*

>>>
[remote "upstream"]
url = https://bitbucket.yanolja.in/scm/pf/global-admin-ui.git
fetch = +refs/heads/*:refs/remotes/upstream/*
fetch = +refs/pull-requests/*/from:refs/remotes/upstream/pr/*
fetch = (target):(로컬에서 내가 사용 할 브랜치 네임) => 위의 예시는 /upstream/pr/xxx 브랜치로 보여진다.

github과 bitbucket 포맷이 다른듯 하다.

기타 추가적으로 alias 추가하여 편하게 사용가능한듯 보이지만, jetbrain 제품에서는 위의 설정만으로도 충분히 편한듯 하다.

https://blog.outsider.ne.kr/1204

