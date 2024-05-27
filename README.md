# Unity_Study_2D_Procedural_Dungoen

학습 자료: https://youtube.com/playlist?list=PLcRSafycjWFenI87z7uZHFv6cUG2Tzu9v&si=dnMCw1ZA2V7zUodQ

#
### ProceduralGenerationAlgorithms.cs
![Direction2D](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2f922656-1275-4b00-9260-fab0d8699753)

Direction2D 클래스를 선언하여, 상하좌우와 대각선 방향들을 향할 Vector2Int 값들을 리스트에 저장함.
GetRandomCardinalDirection 메소드는 지정해둔 상하좌우 4방향의 리스트 중 랜덤으로 1개의 Vector2Int 값을 반환함. 이것은 Random Walk 알고리즘에 이용됨.

![SimpleRandomWalk_Algorithm](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/b69d90c7-e967-487c-b1d8-0de037175798)

Simple Random Walk 알고리즘
HashSet을 이용하여 중복없이 Vector2Int 형식의 경로 값들을 저장함.
이전 좌표를 기준으로 


### TilemapVisualizer.cs
![PaintSingleTile](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2ffba9f4-a7a1-4dc7-b99f-bcd1008f6920)

UnityEngine.Tilemaps가 이용됨.
PaintSingleTile 메소드에서 tilemap의 SetTile 메소드를 이용함.
매개변수로 받은 position을 월드 기준의 좌표 tilePosition으로 설정함.
특정 tilemap에서 지정한 tile을 월드 기준 좌표인 tilePosition 좌표에 배치함.


### 1. Simple Random Walk Result
![SimpleRandomWalk](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/96935aeb-bef1-43c7-8ea3-b8eb70f0b303)

### 2. Corridor First Result
![CorridorFirst](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2674ad1b-6eee-4560-b3e4-7c502dac78f5)

### 3. Rooms First Result
![RoomsFirst](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/060dd119-eeeb-452a-b950-ea6ddc3da8c9)
