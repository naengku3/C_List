# C_List

1.리스트 정의
각 노드가 데이터와 다음 노드를 가리키는 포인터로 이루어진 자료구조

2.리스트 응용
-데이터 저장 : 여러 종류의 데이터를 리스트에 저장하고 필요할 때 해당 데이터에 접근할 수 있다.

-알고리즘 및 데이터 분석 : 다양한 알고리즘 및 데이터 분석 작업에서 사용. 데이터를 정렬, 필터링, 그룹화 및 분석하는 데 활용.

-스케줄링 : 작업 목록을 관리하거나 우선순위 큐를 구현하는 데 활용

-검색 및 필터링 : 리스트에서 특정 항목을 찾거나 조건을 충족하는 항목을 필터링하는 데 사용할 수 있다.
등등 ...

3.리스트를 구현
```c
#include <stdio.h>
#include <stdlib.h>

// 연결 리스트의 노드 구조체 정의
struct Node {
    int data;
    struct Node* next; // 다음 노드의 주소를 저장하는 포인터 
    //(다음 노드주소가 struct Node* 의 형태로 저장)
};

// 노드 추가 함수
void append(struct Node** head, int newData) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = newData; // 새로운 노드의 데이터 필드에 데이터 저장
    newNode->next = NULL; // 새로운 노드의 다음 노드를 NULL로 초기화
    if (*head == NULL) { // *head는 이중포인터의 값을 가리키는 포인터
        *head = newNode; 
        return;
    }
    struct Node* cur = *head;
    while (cur->next != NULL) {
        cur = cur->next; // 다음노드로 이동
    }
    cur->next = newNode; //새 노드의 주소를 next 포인터에 저장
}

// 연결 리스트 출력 함수
void printList(struct Node* head) {
    struct Node* cur = head;
    while (cur != NULL) {
        printf("%d -> ", cur->data); //데이터 출력
        cur = cur->next;
    }
    printf("NULL\n"); //마지막 NULL 출력
}

int main() {
    struct Node* List = NULL; //구조체 포인터로 선언하고 NULL로 초기화

    // 연결 리스트에 데이터 추가
    append(&List, 1);
    append(&List, 2);
    append(&List, 3);
    // 연결 리스트 출력
    printf("Linked List: ");
    printList(List);
    // 메모리 해제
    struct Node* cur = List;
    while (cur != NULL) {
        struct Node* next = cur->next;
        free(cur);
        cur = next;
    }
    return 0;
}
```
설명은 주석으로 추가하였습니다.
