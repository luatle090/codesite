---
title: "Vim"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Sử dụng VIM


VIM có 3 mode: Normal, Insert, Visual

#### Định nghĩa:  
\# là sẽ gõ number ý chỉ số 12 hoặc 35 hoặc 350 ...
			
() là các dấu "", {}, '', ...			

Command: Phím ESC để quay về normal mode, sử dụng phím : để gõ command

:q : để thoát VIM

:q!: Thoát và ko save

:w : Save tập tin

:wq : Save và thoát

:set number : Hiển thị number line (Line tuyệt đối)

## 1. Normal mode:

### &nbsp;&nbsp;Di chuyển:
hjkl : h left, j down, k up, l right

### &nbsp;&nbsp; Di chuyển theo từ
w: di chuyển tới vị trí đầu của từ. 

    Nhấn w sẽ đi tới f ( i i = 0 ; i < 1 ; i +	
    vd: for (int i = 0; i < 10; i++)

W: di chuyển đầu vị trí của token. 1 token là (int 

    token: for (int i = 0; i < 10; i++)
    vd: for (int i = 0; i < 10; i++)

b/B giống như w nhưng đi ngược. 

    Nhấn b sẽ đi tới + i ; 1 < i ; 0 = i i ( f	
    vd: for (int i = 0; i < 10; i++)
	
e/E giống w nhưng con trỏ di chuyển tới cuối của từ. 
		
    Nhấn e sẽ đi tới r ( t = 0 ; i < 0 ; i ) 
	vd: for (int = 0; i < 10; i++) 

### &nbsp;&nbsp; Di chuyển trong tập tin và dòng
gg: di chuyển về đầu tập tin

G: Di chuyển về cuối tập tin

$: di chuyển về đầu dòng kể cả khoảng trắng

0: di chuyển về cuối dòng kể cả khoảng trắng

^: di chuyển tới đầu vị trí character đầu tiên trong dòng

#G : di chuyển tới vị trí # trong tập tin


### &nbsp;&nbsp; Undo
u : sẽ undo toàn bộ last save trong edit mode.
Nếu edit mode gõ hello world. Thoát edit mode sẽ undo toàn bộ hello world

### &nbsp;&nbsp; Redo:
ctrl + r: phương thức giống undo

### &nbsp;&nbsp; Delete Or Cut (sử dụng combie với các phím di chuyển):
x: xóa or cut từng chữ

dw: xóa or cut từ

dW: xóa or cut token

dd: xóa or cut toàn bộ line

d$: xóa or cut từ vị trí con trỏ tới cuối dòng kể cả khoảng trắng

d0: xóa or cut từ vị trí con trỏ lên đầu dòng kể cả khoảng trắng

d^: xóa or cut trước vị trí con trỏ lên vị trí đầu tiên của character 

di()  (delete inside ngoặc): xóa or cut toàn bộ nội dung trong dấu ngoặc

da()  (delete around ngoặc): xóa or cut toàn bộ ngoặc và nội dung bên trong ngoặc. Tương đương lệnh d%

:%d: delete or cut toàn bộ tập tin

dat (delete around tag): xóa toàn bộ tag và nội dung trong tag trong html

dit (delete inside tag): xóa nội dung bên trong tag trong html

:#,#d: delete từ dòng # đến dòng #. Số dòng canh theo bên trái

---- 

cc: Xóa or cut toàn bộ dòng nhưng sẽ vào insert mode 
Các chức năng còn lại như d riêng :%c ko nên dùng, vì bất tiện

---
s: giống x nhưng sẽ vào insert mode

### &nbsp;&nbsp; Copy: 
yy: copy toàn bộ line (để copy theo bôi đen cần vào visual mode)

:%y: copy toàn bộ tập tin

yi(): copy toàn bộ nội dung trong dấu ngoặc

### &nbsp;&nbsp; Paste
p: Paste sau con trỏ

P: Paste trước con trỏ

ctrl + shift + v: paste từ clipboard sang vim (trong visual)

+p  : trong terminal

### &nbsp;&nbsp; Replace:
r: sử 1 từ

:s/tim_kiem/thay_the: find trong current line và replace từ đầu tiên match

:s/tim_kiem/thay_the/g: find trong current line và replace tất cả trong line

:%s/tim_kiem/thay_the: find trong toàn bộ file và replace từ đầu tiên match 

:%s/tim_kiem/thay_the/g: find trong toàn bộ file và replace tất cả

### &nbsp;&nbsp; Search: Việc di chuyển phụ thuộc vào cách tìm kiếm theo kiểu next or back
sử dụng dấu / : /tim_kiem (tìm kiếm theo kiểu next), 
di chuyển khi search: n đi tới. N đi lui

sử dụng dấu ? : ?tim_kiem (tìm kiếm theo kiểu back),
di chuyển khi search: n di chuyển lui. N di chuyển tới

*: nhảy tới từ tiếp theo

### &nbsp;&nbsp; Kiểm tra dấu ngoặc
%: nhảy tới dấu ngoặc, có thể combie với d or c để xóa block code

d%: Bắt buộc phải Di chuyển tới dấu ngoặc rồi mới sử dụng d%. 
Lệnh này tương dương lệnh da() 
	
	vd: for (let i = 0; i < 10; i++) {
		console.log()
	} . Di chuyển tới dấu ngoặc ( hoặc ) rồi gõ d%
	kết quả: for {
		console.log()
	}

### &nbsp;&nbsp;&nbsp;&nbsp; Merge:
J: merge với dòng bên dưới có khoảng trắng

gJ: merge dòng bên dưới ko có khoảng trắng

## 2. Insert mode:

i: insert mode. Chèn trước từ

a: insert mode. Chèn sau từ

I: insert mode. con trỏ sẽ Di chuyển về ĐẦU CHỮ CÁI ĐẦU TIÊN của dòng

A: insert mode. ngược lại với I. di chuyển về cuối

o: enter và insert mode. 

O: previous enter và insert mode.

ctrl + w: thụt về đầu dòng (nếu có từ phía trước sẽ loại bỏ các từ phía trước, nếu là khoảng trắng thì sẽ bỏ toàn bộ khoảng trắng)

ctrl + d: previous tab cho 1 line

ctrl + t: tab nguyên 1 line

## 3. Visual mode:

Là chế độ bôi đen.

v : chuyển sang visual mode (bôi đen character)

V : chuyển sang visual mode (bôi đen toàn bộ line)

y: copy phần bôi đen

d: delete phần bôi đen

### &nbsp;&nbsp;&nbsp;&nbsp; Lower và upper case
u: lower case

U: upper case

### &nbsp;&nbsp;&nbsp;&nbsp; Bôi đen
aB: bôi đen phần {}

ab: bôi đen phần ()

### &nbsp;&nbsp; Tab
\>: tab

<: previous tab

### &nbsp;&nbsp; Copy from Vim to clipboard:
"*y: bôi đen từ và dùng "*y để copy

## 4. Dùng với visual studio code

### &nbsp;&nbsp; Combie với visual code đa con trỏ:
alt + up/down: di chuyển dòng

ctrl + alt + up/down: tạo đa con trỏ

ctrl + shift + v: paste từ clipboard sang vim (trong visual)