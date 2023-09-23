# test_9_23
#include <stdio.h>
#include <stdlib.h>

typedef struct LNode{
	int data;
	struct LNode* next;
}LNode,*LinkList;
bool InitList(LinkList &L){
	L = (LNode*)malloc(sizeof(LNode));
	if(L == NULL)
		return false;
	L->next = NULL;
	return true;
}
//按位序插入（不带头结点）
bool ListInsert(LinkList &L,int i,int e){
	if(i<1)
		return false;
	if(i == 1){
		LNode* s = (LNode*)malloc(sizeof(LNode));
		s->data = e;
		s->next = L;
		L = s;
		return true;
	}
	LNode* p;
	int j=1;
	p = L;
	while(p != NULL && j<i-1){
		p = p->next;
		j++;
	}
	if( p == NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	s->data = e;
	s->next = p->next;
	p->next = s;
	return true;
}
//指定结点后插
bool InsertNextNode(LNode* p,int e){
	if(p == NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	if(s == NULL)
		return false;
	s->data = e;
	s->next = p->next;
	p->next = s;
	return true;
}
//指定结点前插
bool InsertPriorNode(LNode* p,int e){
	if(p == NULL)
		return false;
	LNode* s = (LNode*)malloc(sizeof(LNode));
	if(s == NULL)
		return false;
	s->next = p->next;
	p->next = s;
	//或者引入temp变量交换
	s->data = p->data;
	p->data = e;
	return true;
}
//按位序删除（带头结点）
bool ListDelete(LinkList &L,int i,int e){
	if(i<1)
		return false;
	LNode* p;
	int j=0;
	p = L;
	while(p != NULL && j<i-1){
		p = p->next;
		j++;
	}
	if( p == NULL)
		return false;
	if( p->next == NULL)
		return false;
	LNode* q = p->next;
	e = q->data;
	p->next = q->next;
	free(q);
	return true;
}
//删除指定结点
bool DeleteNode(LNode* p){
	if( p == NULL)
		return false;
	LNode* q = p->next;
	p->data = p->next->data;
	p->next = q->next;
	free(q);
	return true;
}
//按位序查找
bool GetElem(LinkList L,int i){
	if(i<0)
		return false;
	LNode* p;
	int j=0;
	p = L;
	while(p != NULL && j<i){
		p = p->next;
		j++;
	}
	return p;
}
//按值查找
LNode* LocateElem(LinkList L,int e){
	LNode* p = L->next;
	while(p != NULL && p->data != e){
		p = p->next;
	}
	return p;
}
//求表长
int Length(LinkList L){
	int len = 0;
	LNode* p = L;
	while(p->next != NULL){
		p = p->next;
		len++;
	}
	return len;
}
//头插法
LinkList List_HeadInsert(LinkList &L){
	LNode* p;
	int x;
	L = (LNode*)malloc(sizeof(LNode));
	L->next = NULL;
	scanf("%d",&x);
	while(x != 9999){
		LNode* s = (LNode*)malloc(sizeof(LNode));
		s->data = x;
	    s->next = p->next;
	    p->next = s;
		scanf("%d",&x);
	}
	return L;
}
int main(){
	LinkList L;
	InitList(L);
	LinkList(L,i,e);
	return 0;
}
