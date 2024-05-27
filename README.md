# Unity_Study_2D_Procedural_Dungoen

던전 크롤링 게임을 만들기 위해 던전의 절차적 생성이 필요하여 학습함.

학습 자료: https://youtube.com/playlist?list=PLcRSafycjWFenI87z7uZHFv6cUG2Tzu9v&si=dnMCw1ZA2V7zUodQ

#
### TilemapVisualizer.cs
![PaintSingleTile](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2ffba9f4-a7a1-4dc7-b99f-bcd1008f6920)

ProceduralGenerationAlgorithm을 통해 좌표값들은 TilemapVisualizer에 의해 시각화 됨.

UnityEngine.Tilemaps가 이용됨.

PaintSingleTile 메소드에서 tilemap의 SetTile 메소드를 이용함.

매개변수로 받은 position을 월드 기준의 좌표 tilePosition으로 설정함.

특정 tilemap에서 지정한 tile을 월드 기준 좌표인 tilePosition 좌표에 배치함.

#
### AbstractDungeonGenerator.cs
![Abstract](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/908ee389-01e7-47c1-b0e5-c347c681c482)

해당 학습자료에서는 3종류의 DungeonGenerator를 만들고 확인하므로, 이를 위해 DungeonGenerator를 추상화함.

좌표들을 시각화하기 위한 tilemapVisualizer를 null로 초기화함.

던전 생성의 시작점을 (0,0)으로 초기화함.

GenerateDungeon에서 tilemap을 초기화하고, 각 DungeonGenerator의 절차적 생성을 진행하는 형태를 잡음.

#
### RandomDungeonGeneratorEditor.cs
![Editor](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/e8e84c49-d600-479a-a3a5-1535f2556645)

던전 생성과 결과 확인 과정을 간편하게 만들기 위해서 유니티 에디터를 변경함.

Create Dungeon 버튼을 만들어, Edit mode에서도 던전 생성이 가능하게 만듦.

![generator01](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/1820f28f-e777-4a5e-8cc8-a9078aee196c)

![generator02](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/da1c79c6-c9c4-4a4d-9ee0-adfc583dbf86)

![generator03](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/c6cb1eba-6ac4-4870-9f9a-b8d4d2b282a5)

#
### ProceduralGenerationAlgorithms.cs
![Direction2D](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2f922656-1275-4b00-9260-fab0d8699753)

Direction2D 클래스를 선언하여, 상하좌우와 대각선 방향들을 향할 Vector2Int 값들을 리스트에 저장함.

GetRandomCardinalDirection 메소드는 지정해둔 상하좌우 4방향의 리스트 중 랜덤으로 1개의 Vector2Int 값을 반환함.

이것은 Random Walk 알고리즘에 이용됨.

![SimpleRandomWalk_Algorithm](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/b69d90c7-e967-487c-b1d8-0de037175798)

Simple Random Walk 알고리즘

HashSet을 이용하여 중복없이 Vector2Int 형식의 경로 값들 path에 저장함.

이전 좌표를 기준으로 GetRandomCardinalDirection을 통해 얻은 Vector2Int 값을 더한 좌표를 얻음.

그것을 path에 추가하고, 새 좌표를 시작점으로 설정함.

매개변수를 통해 얻은 walkLength 횟수만큼 이를 반복함.

반복이 끝난 이후 모든 좌표값들이 들어있는 path를 반환함.

![RandomWalkCorridor_Algorithm](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/35769814-8f08-46d6-b889-7260a77199ef)

Random Walk 알고리즘을 이용하여, 

![BSP_Algorithm](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/3d3e8b93-b2a8-428e-b040-4e57bd6527b2)

BSP(Binary Space Partitioning, 이진 공간 분할법) 알고리즘


![Split](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/06f0d34e-b251-4389-9693-635ddf1198aa)





### 1. Simple Random Walk Result
![SimpleRandomWalk](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/96935aeb-bef1-43c7-8ea3-b8eb70f0b303)

Random Walk 알고리즘을 이용하여 생성된 단일 방.

### 2. Corridor First Result
![CorridorFirst](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2674ad1b-6eee-4560-b3e4-7c502dac78f5)

Random Walk 알고리즘을 이용하여 생성된 다수의 방과 통로.

### 3. Rooms First Result
![RoomsFirst](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/060dd119-eeeb-452a-b950-ea6ddc3da8c9)

BSP 알고리즘을 이용하여 생성된 다수의 방과 통로.
