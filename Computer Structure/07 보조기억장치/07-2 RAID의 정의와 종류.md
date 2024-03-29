### RAID의 정의

우리가 아는 사실 : '보조기억장치에도 수명이 있다.'
그럼 수백 TB데이터는 서버에 저장될 텐데 어떻게 잃어버리지 않는다고 확신할 수 있을까?

=> **RAID**로 해결!
Redundant Array of Independent Disks
- 하드디스크와 SSD를 사용하는 기술
- 안정성, 높은 성능을 위해 => **여러 개의 물리적 보조기억장치를 마치 하나의 논리적 보조기억장치처럼 사용하는 기술**

#### RAID 종류
RAID 구성방법 : RAID 레벨이라고 한다.
- RAID 0, 1, 2, 3, 4, 5, 6, 10 ...

#### RAID 0
여러 개의 보조기억 장치에 데이터를 단순히 나누어 저장하는 구성방식
=> 번갈아가며 데이터를 저장
![[Pasted image 20240219132940.png]]
**스트라입** : 줄무늬처럼 분산되어 저장된 데이터
**스트라이핑** : 분산하여 저장하는 것 => 데이터를 읽고 쓰는 속도가 빨라진다.
여러 번 걸쳐 읽고 썼을 데이터 => 동시에 읽고 쓸 수 있다.

이론상 : 4TB 한개보다 RAID0이 4배 빠르다.

단점 
- 하드 디스크 중 하나가 문제가 생기면 모든 정보를 읽는 데 문제가 생길 수 있다.

#### RAID1
복사본을 만드는 방식 : **미러링**
![[Pasted image 20240219133204.png]]
장점 : 복구가 매우 간단하다.
- 하나에 문제가 발생해도 잃어버린 정보를 금방 되찾을 수 있음
단점 : 용량이 적어진다(0에 비해)
- 복사본이므로, 많은 양의 하드디스크가 필요하다 => 비용의 증가

#### RAID 4
완전한 복사본이 아닌, 오류를 검출하고 복구하기 위한 정보를 저장한 장치를 두는 구성방식 : **패리티 비트**
![[Pasted image 20240219133424.png]]
오류검출 + 복구까지
- 1보다 적은 용량으로 데이터를 안전하게 보관할 수 있다.
1. RAID 4에서는 패리티 정보를 저장한 장치로써 나머지 장치들의 오류를 검출+복구한다.
2. 본래 오류 검출용 정보지만, RAID에서는 오류 복구도 가능하다.
문제점 : 새로운 데이터가 저장될 때마다, 패리티 저장하는 디스크에도 데이터를 쓰니까 => 패리티 저장장치에 **병목현상**이 생긴다.

#### RAID 5
패리티 정보를 하드디스크 1개씩 분산하여 저장한다.

![[Pasted image 20240219134321.png]]

#### RAID 6
RAID 5와 같으나, 서로 다른 두 개의 패리티는 두는 방식
=> 오류 검출 + 복구 수단이 2개
속도 : RAID5보다 느리다
데이터를 조금 희생하더라도 안전하게 보관하고 싶을 때!
![[Pasted image 20240219134447.png]]

