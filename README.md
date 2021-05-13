 !----------------------------------THIS IS NOW THE EDITED PART RIGHT HERE----------------------------!

#include <iostream>
#include<stdlib.h>
#include<stdio.h>

using namespace std;

struct Node {
	string data;
	struct Node* link;
};

bool isEmpty(Node* top){
	if (top == NULL){
		return true;
	}
	return false;
}

/// inserts kitchenware at the top
Node* addWare(Node* top, string kitchenware){
	struct Node* temp = new Node();
	temp->data = kitchenware;
	temp->link = top;
	top = temp;
}

/// deletes the top of stack
Node* washWare(Node* top, string data){
	if (isEmpty( top)){
		cout << "\n The stack is empty. No more kitchenwares to wash." << endl;
		return NULL;
		///since code's being read from top to bottom, di ko na kailangan ng return value
		//dito if papasok sya sa if statement..?? debug: error.
	}
	struct Node* temp = top;
	top = top->link;
	cout << "\n" << temp->data << " is being washed" << endl;
	free(temp);
	return top;	
}

/// deletes all stack
Node* washWareAll(Node* top, string data){ 
	
 	while(top != NULL){
 		struct Node*  temp = top;
 		top = top->link;
 		cout << "\n " << temp->data << " is being washed." << endl; 
 		free(temp);	
	 }
	 if (isEmpty( top)){
		cout << "\n The stack is empty. No kitchenwares to be washed." << endl;
		return NULL;
 	} 
}

/// prints what is at the top of stack
Node* washWareTop(Node* top, string data){ 
	struct Node* temp = top;
	if (isEmpty( top)){
		cout << "\n The stack is empty. No kitchenwares to wash." << endl;
		return NULL;
	}
	cout << "\n" << temp->data << " is next to be washed." << endl;
	return top;
}

/// for checking only
void print(Node* top){
	if (isEmpty( top)){
		cout << "\n There are no kitchenwares to be washed." << endl ;
		return;
	}
	cout << "\n your list: \n" << endl;
	while(top != NULL){
		cout << top->data << endl;
		top = top->link;
	}
}

int main(){
	Node* top = NULL;
	int choice;
	string kitchenware;
	
	cout << "\n\n  Dishwasher program - A stack implementation.\n" << endl;
selection:
	cout << "\n\n LIST MENU \n [1] ADD KITCHENWARE \n [2] WASH KITCHENWARE \n [3] TOP KITCHENWARE\n [4] WASH ALL \n [5] EXIT \n [6] PRINT \n" << endl;
	cout << " Choice: ";
	cin >> choice;
	
	switch (choice){
		
		case 1:
			cout << "\n Enter the kitchenware to be added: ";
			cin >> kitchenware;
			top = addWare(top, kitchenware);
			break;
			
		case 2:
			top = washWare(top, kitchenware);
			break;
			
		case 3:
			top = washWareTop(top, kitchenware);
			break;
		
		case 4:
			top = washWareAll(top, kitchenware);
			break;		

		case 5:
			return 0;
			
		case 6:
			print(top);
			break;
			
		default:
			cout << " Enter from the selection only!" << endl;
			
	}
	goto selection;
	
}

///debug:
/// naga work na ang code pero malli yung name na gina displayyyy!!!!!!!! whyyyy????
///may mali...after ko ma wash all. no more na dapat pero pag press ko ng top wash andun parin si three.. ?? workingg
/// may mali sa top ko..gina delete nya ung top.. workinggg
//// may mali sa wash all kooo.. di nya gina delete yung mga data
/// mali yung namae na gina displayyy ni washall
/// sa wakas thank you lord nag gana na ung wash all samoka!!!
/// for the first time naka pasa ako ng program na working lahat!!! minus nga lang.. pero!! atleast! woooh achievement unlocked!!
