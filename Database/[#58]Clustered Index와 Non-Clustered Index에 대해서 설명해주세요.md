## 1. Clustered Index와 Non-Clustered Index에 대해서 설명해주세요

    Clustered Index는 테이블의 컬럼중 하나를 지정하여 Index로 설정하고, 물리적으로 테이블의 데이터를 재배열하는 것을 말합니다.
    저장된 순서에 상관없이 지정된 index에 따라 정렬되며, key값으로 바로 데이터를 탐색합니다.
    따라서 테이블 당 하나의 Clustered Index만 존재할 수 있으며, PK는 초기에 Clustered Index로 생성됩니다.
    또한 물리적으로 정렬되어있기 때문에, 빠른 속도를 보입니다.

    반면, Non-Clustered Index는 물리적으로 데이터를 정렬하지 않고, 별도의 데이터 페이지를 구성하는 것을 말합니다.
    따라서 테이블 당 여러개의 Non-Clustered Index가 존재할 수 있으며, 데이터에 대한 포인터를 갖고 있습니다.
    Clustered Index보다 속도가 느리고 더 많은 메모리를 사용하지만, 데이터의 입력-수정-삭제시에는 더 빠른 속도를 보입니다.

## 2. Clustered Index은 어떻게 동작하나요?

    먼저 하나의 컬럼을 Clustered Index으로 선정하면, Index 순으로 테이블이 정렬됩니다.
    그 후 Root페이지와 Reaf페이지로 이루어진 Index 페이지로 구성됩니다.
    Root페이지의 경우, Index Key와 Reaf 페이지의 번호를 갖고있으며 Index key에 따라 탐색해야 할 Reaf페이지를 매핑하는 역학을 합니다.
    Reaf페이지는 데이터를 갖고 있는 페이지입니다.
    
    만약 Clustered Index를 이용한 탐색을 한다면, 먼저 Root페이지에서 탐색할 Index Key가 포함된 범위를 가진 Reaf 페이지를 찾습니다.
    그 후 해당 Reaf 페이지를 탐색하여 목적 데이터를 찾을 수 있습니다.

    반면, 입력/수정/삭제가 이루어지는 경우에는 Clustered Index의 정렬 순서에 맞게 입력/수정/삭제가 이루어져야 합니다..
    입력시 올바른 위치를 탐색해서 삽입이 이루어지고, 수정이나 삭제시에는 재정렬이 이루어집니다.
    또한 입력으로 Reaf 페이지의 범위를 초과하게 되면, Reaf 페이지를 분할해야 합니다.. 

    따라서 탐색의 경우 Non-Clustered Index보다 빠른 속도를 보여주지만, 
    실제 데이터의 정렬이 이루어지기 때문에 입력/수정/삭제의 경우 더 느린 속도를 보여줍니다..    


## 3. Non-Clustered Index은 어떻게 동작하나요?

    Non-Clustered Index는 기존의 데이터 테이블을 건들지 않고 동작합니다.

    Root페이지와 Reaf페이지로 이루어진 별도의 Index 페이지를 생성합니다.
    그리고 Reaf 페이지에는 데이터가 담기지 않고, 기존 데이저 테이블에 있는 데이터의 위치를 가리키는 포인터를 저장합니다.
    즉, Root페이지는 Index Key와 Reaf 페이지의 번호를 갖고, Reaf페이지는 Index와 실제 데이터의 위치를 가리키는 포인터를 갖도록 구성됩니다.

    따라서 탐색의 경우, 실제 데이터를 찾아 포인터로 이동해야하기에 Clustered Index보다 느린 속도를 보입니다.
    반면, 입력/수정/삭제의 경우에는 실제 데이터 테이블을 재정렬할 필요하 없으므로 Non-Clustered Index에 대한 변경작업의 적습니다..
    그래서 Clustered Index에 비해 더 빠른 속도를 보여줍니다..
