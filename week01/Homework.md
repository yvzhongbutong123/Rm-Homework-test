# 第一周作业：上传你的rm_study并且实现一个装甲板数据排序功能

## 输入：
	第 1 列：装甲板编号（整数）
	第 2 列：距离，单位米（非负小数）
	第 3 列：偏角，单位度，可以是负数

## 输出：
	每一行：id=x 距离=x m
	注意距离中的x与单位m之间有空格

## 样例：

### 输入：
	1 3.2 12.5
	2 1.8 -4.0
	3 5.0 20.1
	4 2.4 0.0

### 输出：
	id=2 距离=1.80 m
	id=4 距离=2.40 m
	id=1 距离=3.20 m
	id=3 距离=5.00 m

## 要求：
	从一个空目录开始，搭出这个结构：
	rm_study/
	├─ src/main.cpp
	├─ src/armor.h
	├─ src/armor.cpp
	├─ data/armor.txt
	├─ CMakeLists.txt
	├─ .gitignore
	└─ README.md

## 代码提供：
	// armor.h
	#pragma once
	#include <string>
	#include <vector>
	struct Armor {
		int    id       = 0;
		double distance = 0;   // 米
		double angle    = 0;   // 度
	};
	std::vector<Armor> loadArmors(const std::string& path);   // 读文件
	void sortByDistance(std::vector<Armor>& armors);          // 按距离排序
	void printArmors(const std::vector<Armor>& armors);       // 打印

	// main.cpp
	#include "armor.h"
	#include <iostream>
	int main() {
		auto armors = loadArmors("data/armor.txt");
		if (armors.empty()) {
			std::cout << "没读到数据，检查路径\n";
			return -1;
		}
		sortByDistance(armors);
		printArmors(armors);
		return 0;
	}
	实现以上的三个函数