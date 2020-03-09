# awk 명령어

 - Linux 파일 텍스트의 데이터 검사, 조작, 출력 을 할 수 있다.
 - 사용해 보니 awk 명령어만 잘 사용하면 원하는 데이터를 거의 모두 추출 할 수 있을거 같다.
 
---

### 사용 예

 - 기본 출력
```shell script
 sangjaekim@gimsangjaeui-MacBookPro  /  df -h
Filesystem                                                                      Size   Used  Avail Capacity iused      ifree %iused  Mounted on
/dev/disk1s5                                                                   233Gi   10Gi  130Gi     8%  484184 2447617136    0%   /
devfs                                                                          191Ki  191Ki    0Bi   100%     662          0  100%   /dev
/dev/disk1s1                                                                   233Gi   91Gi  130Gi    42% 1202798 2446898522    0%   /System/Volumes/Data
/dev/disk1s4                                                                   233Gi  2.0Gi  130Gi     2%       2 2448101318    0%   /private/var/vm
map auto_home                                                                    0Bi    0Bi    0Bi   100%       0          0  100%   /System/Volumes/Data/home
```

 - 2,3,4 열만 출력 (탭으로 구분)
 ```shell script
 sangjaekim@gimsangjaeui-MacBookPro  /  df -h | awk '{print $2 "\t" $3 "\t" $4}'
Size	Used	Avail
233Gi	10Gi	130Gi
191Ki	191Ki	0Bi
233Gi	91Gi	130Gi
233Gi	2.0Gi	130Gi
auto_home	0Bi	0Bi
Studio	Code.app	233Gi
 ```

 - 사용한 용량이 5Gb 이하인 경로 모두 출력
 ```shell script
 sangjaekim@gimsangjaeui-MacBookPro  /  df -h | awk ' $3 < 5Gi { print }'
/dev/disk1s5                                                                   233Gi   10Gi  130Gi     8%  484184 2447617136    0%   /
devfs                                                                          191Ki  191Ki    0Bi   100%     662          0  100%   /dev
/dev/disk1s4                                                                   233Gi  2.0Gi  130Gi     2%       2 2448101318    0%   /private/var/vm
map auto_home                                                                    0Bi    0Bi    0Bi   100%       0          0  100%   /System/Volumes/Data/home
 ```

참조자료 : <https://recipes4dev.tistory.com/171>