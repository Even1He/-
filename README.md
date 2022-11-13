# 学习结构体与链表
```
#include<iostream>
using namespace std;
struct Node
{
	int value;		
	Node* next;		//结构体中定义的指针//
	Node(int _value):value(_value),next(NULL){}		//结构体中的构造函数//
};

int main()
{
	Node* p = new Node(1);		//动态开辟一个新的地址//
	Node* q = new Node(2);		//这里的 new ,是一个函数，专门用来开辟一个链表的一个节点并有相应的地址使得一个指针可以指向这个开辟出来的一个地址//
	Node* o = new Node(3);		//（）这个括号里面的数字就是结构体中的value的值，只不过在构造函数中构造出一个_value这个临时变量给value赋值而已//
	p->next = q;
	q->next = o;
	
	Node* head = p;		//头结点的设置，以第一个结点来作为头结点//

	//链表的遍历//
	cout << "初始链表" << endl;
	for (Node* i = head; i ;i = i->next)
	{
		cout << i->value << ' ';
	}

	cout << endl;

	//在链表中添加一个结点(将这个新的结点插在链表的首位//
	Node* u = new Node(5);		//定义一个新的结点//
	u->next = p;	//再将这个新的结点指向头结点，使得要将这个新加上去的结点与原链表相联系//
	head = u;	//再将头结点转移到这个新的节点上面，为新的链表的遍历做准备//

	cout << "在首部添加一个新的结点" << endl;
	for (Node* i = head; i; i = i->next)
	{
		cout << i->value << ' ';
	}
	cout << endl;
	//若将这个新的结点插在别的位置//
	Node* z = new Node(7);
	z->next = q;
	p->next = z;
	cout << "在其他位置添加一个新的结点" << endl;
	for (Node* i = head; i; i = i->next)
	{
		cout << i->value << ' ';
	}

	//若要实现在链表中删除结点//
	//那么在遍历链表时，跳过这个结点,去遍历下一个结点即可//
	//若要跳过数据域是2的结点//
	cout << endl;
	cout << "当删除数据域为2的结点后的链表" << endl;
	z->next = z->next->next = o;
	for (Node* i = head; i; i = i->next)
	{
		cout << i->value << ' ';
	}
	return 0;
}
```
