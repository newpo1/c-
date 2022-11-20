# c-
二分算法左闭右开疑问
//左闭右开---正确书写
int Solution1(vector& vec, int target) {
int left = 0, right = vec.end() - vec.begin();
while (left < right) {
int middle = (left + right) / 2;
if (vec[middle] > target) {
right = middle;
}
else if (vec[middle] < target) {
left = middle + 1;
}
else {
return vec[middle];
}
}
return -1;
};
//左开右闭----修改后
int Solution1(vector& vec, int target) {
int left = 0, right = vec.end() - vec.begin();
while (left < right) {
int middle = (left + right) / 2;
if (vec[middle] > target) {
right = middle-1;
}
else if (vec[middle] < target) {
left = middle;
}
else {
return vec[middle];
}
}
return -1;
};

问题：与第一个代码不同的是right = middle-1;和left = middle;开始我认为这样改也是正确的。但我现在认为这样修改代码可能会存在left一直在同一个middle让程序进入循环无法退出。有大佬帮我解答一下这样写正确吗，如果是错误的那我认为的错误原因对吗？
我认为错误的证明：
((left+right)/2)-0.5=left 这里减0.5是因为如果得到的是一个double型类似3.5则因为int会转为3
left=right-1;这种情况下代码会一直循环。
