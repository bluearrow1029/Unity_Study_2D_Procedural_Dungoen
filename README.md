# Unity_Study_2D_Procedural_Dungoen

던전 크롤링 게임을 만들기 위해 던전의 절차적 생성이 필요하여 학습함.

학습 자료: https://youtube.com/playlist?list=PLcRSafycjWFenI87z7uZHFv6cUG2Tzu9v&si=dnMCw1ZA2V7zUodQ

#
### 결과물

### 1. Simple Random Walk
![SimpleRandomWalk](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/96935aeb-bef1-43c7-8ea3-b8eb70f0b303)

Random Walk 알고리즘을 이용하여 생성된 단일 방.

### 2. Corridor First
![CorridorFirst](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2674ad1b-6eee-4560-b3e4-7c502dac78f5)

Random Walk 알고리즘을 이용하여 생성된 다수의 방과 통로.

### 3. Rooms First
![RoomsFirst](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/060dd119-eeeb-452a-b950-ea6ddc3da8c9)

BSP 알고리즘을 이용하여 생성된 다수의 방과 통로.

#
### 코드 설명

### WallTypesHelper.cs
![WallTypes](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2683a4f6-f213-4825-bbda-4ddbfc0e17da)

WallTypesHelper에 입력된 바이너리 데이터 분류들 중 일부.

입력받는 바이너리 데이터를 비교하여, 타일의 종류를 구분하기 위해 이용됨.

![image](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/a17b4c1b-7361-4f39-9389-3abd7624c682)

바이너리 데이터는 12시 타일부터 시계방향 순서로 입력됨.

바닥 타일이면 1이 입력되고, 바닥 타일이 아니면 0이 입력됨.

#
### TilemapVisualizer.cs
![PaintSingleTile](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/2ffba9f4-a7a1-4dc7-b99f-bcd1008f6920)

ProceduralGenerationAlgorithm을 통해 좌표값들은 TilemapVisualizer에 의해 시각화 됨.

UnityEngine.Tilemaps가 이용됨.

PaintSingleTile 메소드에서 tilemap의 SetTile 메소드를 이용함.

매개변수로 받은 position을 월드 기준의 좌표 tilePosition으로 설정함.

특정 tilemap에서 지정한 tile을 월드 기준 좌표인 tilePosition 좌표에 배치함.

![PaintSingleBasicWall](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/ed8cef0f-fdb4-4874-bbe7-c5d81745d10c)

기본 벽(상하좌우 4방향 벽)을 시각화 하기 위한 메소드

매개변수로 받은 바이너리 데이터가 포함되어있는 곳에 따라서 타일의 종류가 설정됨.

이후, 타일이 null이 아니면 설정된 종류의 타일을 배치함.

![PaintSingleCornerWall](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/d4144a0b-ceef-47a7-b457-af32ae184bf8)

모서리 벽을 시각화 하기 위한 메소드

매개변수로 받은 바이너리 데이터가 포함되어있는 곳에 따라서 타일의 종류가 설정됨.

이후, 타일이 null이 아니면 설정된 종류의 타일을 배치함.

#
### AbstractDungeonGenerator.cs
![Abstract](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/908ee389-01e7-47c1-b0e5-c347c681c482)

해당 학습자료에서는 3종류의 DungeonGenerator를 만들고 확인하므로, 이를 위해 DungeonGenerator를 추상화함.

좌표들을 시각화하기 위한 tilemapVisualizer를 null로 초기화함.

던전 생성의 시작점을 (0,0)으로 초기화함.

GenerateDungeon에서 tilemap을 초기화하고, 각 DungeonGenerator의 절차적 생성을 진행하는 형태를 잡음.

#
### SimpleRandomWalkSO.cs
![ScriptableObject](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/1e58e798-8449-4259-b964-0f8f3e33efb7)

던전 생성에 이용할 iteration값과 walkLength값을 미리 설정할 수 있는 ScriptableObject를 생성.

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

방들을 잇기 위한 복도 생성 알고리즘.

현재 좌표를 복도 좌표(corridor)에 추가함.

상하좌우 4방향 중 랜덤 1방향으로 방향(direction)을 지정함.

매개변수로 받은 corridorLength만큼 지정된 방향(direction)으로 좌표를 한칸씩 이동.

그 과정 중, 현재 좌표들을 복도 좌표(corridor)에 추가.

복도 좌표(corridor)를 반환함.

![BSP_Algorithm](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/3d3e8b93-b2a8-428e-b040-4e57bd6527b2)

BSP(Binary Space Partitioning, 이진 공간 분할법) 알고리즘.

던전 전체의 BoundsInt를 roomsQueue에 추가함.

방 크기 최소 설정값보다 크고, 작음과 랜덤값과의 크고 작음으로 분기를 나눔.

조건에 맞춰서 수직 분할이나 수평 분할을 수행하거나, 더이상 나눌 수 없다면 roomsList에 추가함.

이를 roomsQueue가 0이 될 때까지 반복함.

![Split](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/06f0d34e-b251-4389-9693-635ddf1198aa)

수직 분할(SplitVertically)

xSplit 값을 지정하여 기존 BoundsInt를 수직으로 나눠서 2개의 방의 BoundsInt를 roomsQueue에 추가함.

수평 분할(SplitHorizontally)

ySplit 값을 지정하여 기존 BoundsInt를 수평으로 나눠서 2개의 방의 BoundsInt를 roomsQueue에 추가함.

#
### WallGenerator.cs
![CreateWalls](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/c8ebf573-79a8-4d49-8307-7a25800b6b2d)

FindWallsInDirections 메소드를 통하여 상하좌우 벽 타일들의 좌표들과 대각선 벽 타일들의 좌표들을 구함.

CreateBasicWall로 상하좌우 벽들을 시각화함.

CreateCornerWalls로 대각선 벽들을 시각화함.

![FindWalls](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/a290f22c-2124-4fb0-a8e5-80d4bf75a5db)

HashSet으로 중복없는 벽 좌표값들(wallPositions)을 구함.

모든 바닥 좌표에서 상하좌우 벡터 이동한 좌표(neighbourPosition, 이웃 좌표)를 구하고, 그 좌표가 바닥 좌표인지 아닌지 확인함.

바닥 좌표가 아니라면, 벽 좌표에 추가함.

![CreateBasicWall](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/a7822ebb-b89f-43c8-9081-0b80f06b6ba6)

상하좌우 중 어느 방향의 벽인지 판별하고, 시각화하기 위한 메소드.

벽 좌표들의 상하좌우 인접한 좌표들이 바닥 좌표인지 확인.

바닥좌표라면, 바이너리 데이터에 1 추가.

아니라면, 바이너리 데이터에 0 추가.

바이너리 데이터를 기반으로 시각화함.

![CreateCornerWalls](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/c339d060-6e20-4ccb-99a2-e7afb116f838)

모서리 벽의 방향을 판별하고, 시각화하기 위한 메소드.

모서리 벽 좌표들을 중심으로 인접한 8방향 좌표들이 바닥 좌표인지 확인.

바닥좌표라면, 바이너리 데이터에 1 추가.

아니라면, 바이너리 데이터에 0 추가.

#
### SimpleRandomWalkDungeonGenerator.cs
![RunRandomWalk](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/6b6b010b-12e8-484e-b77c-4ae549bb7457)

현재 좌표(currentPosition)에서 ScriptableObject의 walkLength 값으로 SimpleRandomWalk를 수행함.

얻은 좌표값들(path)을 중복이 없게 바닥타일(floorPositions)에 추가함. 

생성한 바닥타일들의 좌표들 중 하나로 현재 좌표를 변경함.

이것을 ScriptableObject의 iterations 값만큼 반복하고 끝나면 floorPosition을 반환함.

타일맵 초기화 후, 반환된 floorPositions 좌표값들로 바닥 타일들을 시각화함.

CreateWalls를 수행하여 벽 타일들도 시각화함.

#
### CorridorFirstDungeonGenerator.cs
![CorridorFirstGeneration](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/7fa13b95-4be0-4e8d-bc71-972b32a9aa0e)

CreateCorridors 메소드로 얻은 복도 좌표를 바닥 좌표(floorPositions)에 추가.

CreateRooms 메소드로 얻은 좌표들을 방 좌표(roomPositions)로 설정.

막다른 길의 좌표들을 구하고, 그 좌표로 CreateRoomsAtDeadEnd 메소드를 실행.

메소드에 의해, 막다른 길에서 생성한 방들의 좌표가 roomPosition에 추가됨.

바닥 좌표(floorPositions)에 추가하고, 이를 기준으로 바닥과 벽 타일들을 시각화함.

![CreateRoomsAtDeadEnd](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/b673f8e9-8205-49c9-b655-161a81b1fb75)

막다른 길(DeadEnd)에 방을 생성하는 메소드

모든 막다른 길 좌표 중, 방 좌표에 추가된 곳이 아니면 Random Walk 실행.

얻은 좌표들을 방 좌표(roomFloors)에 추가.

![FindAllDeadEnds](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/55302665-ca43-431e-b55d-6a8362da73b9)

모든 막다른 길(DeadEnd)을 탐색하는 메소드

모든 바닥좌표에서 상하좌우 4방향으로 이어지는 인접한 바닥좌표이 있을때마다 카운트(neighbourCount) 1 증가

카운트(neighbourCount)가 1인 경우, 막다른 길 좌표(deadEnds)에 추가.

모든 탐색이 끝난 이후, 막다른 길 좌표(deadEnds) 반환.

![CreateRooms](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/423d507a-b827-43cd-9cf8-969a0b91850d)

potentialRoomPositions 좌표의 개수에 roomPercent 배율 곱한 값을 반올림한만큼 방 생성 횟수를 정함.

생성할 방의 좌표들을 Guid.NewGuid() 기준으로 내림차순으로 정렬함.

방 좌표마다 Random Walk를 실행하고, 방 좌표(roomPositions)에 추가함.

방 좌표들을 반환함.

![CreateCorridors](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/78467708-efd6-4e32-9e6c-32308912869e)

Random Walk Corridor로 반환된 복도 좌표들을 구함.

복도 좌표 중 마지막 좌표를 현재 좌표로 potentialRoomPositions에 추가함.

그 후, 복도 좌표를 바닥 좌표(floorPositions)에 추가함.

이를 CorridorCount만큼 반복함.

#
### RoomFirstDungeonGenerator.cs
![CreateRoomss](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/33ab2a86-7eb1-4c8f-a809-51ea83caf650)

BSP 알고리즘을 이용한 방 생성 메소드.

방 랜덤 생성(randomWalkRooms)의 체크 여부에 따라서 CreateSimpleRooms나 CreateRoomsRandomly를 실행함.

모든 방 좌표에서 방의 중심 좌표를 구하고 roomCenters에 추가함.

방 중심 좌표인 roomCenters로 ConnectRooms 메소드를 실행하고, 복도 좌표를 구하여 바닥 좌표에 추가함.

바닥 좌표들과 벽 좌표들을 시각화함.

![CreateRoomRandomly](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/973a87a9-9208-4ec0-8b46-0c5262a5fb32)

x 좌표와 y 좌표를 반올림하여 방 중심 좌표를 구함.

방 중심에서 Random Walk를 실행하여 방 좌표들을 구함.

모든 방 좌표들 중, 방 크기의 최소값과 오프셋 설정에 부합한 좌표들을 바닥 좌표에 추가함.

모든 바닥 좌표들을 반환함.

![ConnectRooms](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/e7cea373-1c4e-4f08-b751-4773fc8c369c)

모든 방 중심점 중, 랜덤 하나를 기준으로 시작함.

FindClosestPointTo 메소드로 가장 가까운 중심점을 구함.

CreateCorridor 메소드로 두 중심점을 잇는 바닥 좌표들을 구하고, 복도 좌표에 추가함.

모든 복도 좌표들을 반환함.

![CreateCorridor](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/b101e83f-cf27-4e43-8980-cb7148c6d8fa)

현재 방 중심의 y 좌표와 목적지인 중심의 y 좌표가 다르면, (0,1)이나 (0,-1)을 더해주고 그 좌표를 복도 좌표에 추가함.

이를, 두 중심의 y 좌표가 같아질 때까지 반복함.

현재 방 중심의 x 좌표와 목적지인 중심의 x 좌표가 다르면, (1,0)이나 (-1,0)을 더해주고 그 좌표를 복도 좌표에 추가함.

이를, 두 중심의 x 좌표가 같아질 때까지 반복함.

모든 복도 좌표들을 반환함.

![FindClosestPointTo](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/fd7b4219-5d2f-498c-893b-52bb4de9d2b3)

현재 방 중심점과 모든 방의 중심점의 거리를 비교하여 가장 가까운 중심의 좌표를 closest에 대입.

closest를 반환함.

![CreateSimpleRooms](https://github.com/bluearrow1029/Unity_Study_2D_Procedural_Dungoen/assets/47950172/4d001e8f-8a86-42aa-a463-08f5d5fcb464)

모든 방 좌표에서 설정한 오프셋과 방의 크기만큼 바닥 좌표를 새롭게 구함.

바닥 좌표들을 반환함.
