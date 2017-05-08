#include "stdafx.h"
#include <fstream>  
#include <string> 
#include<vector>
#include<iomanip>
#include<iostream>
#include"std_lib_facilities.h"
using namespace std;
#include <memory>
#include<map>;

void countwords(vector<string>& words,map<string, int>& counting,int n) 
{
	for (string word : words) 
	{ 
		if (word.size() < n)continue;
		counting[word.substr(word.length() - n)]++;
	}
}

int main() 
{
	map<string, int> counting;
	cout << "enter n of n-letter suffix:";
	int n;
	cin >> n;
	ifstream infile;
	infile.open("dictionary.txt");
	vector<string> words;
	string word;
	while (getline(infile, word))
	{
		words.push_back(word);
	}
	infile.close();

	countwords(words, counting, n);
	vector<int>numsize;
	for (string word : words)
	{
		numsize.push_back(counting[word.substr(word.length() - n)]);
	}
}
