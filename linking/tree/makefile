cur.dir := .
inc.dir := $(cur.dir)/inc
bin.dir := $(cur.dir)/bin
lib.dir := $(cur.dir)/lib
obj.dir := $(cur.dir)/obj
scr.dir := $(cur.dir)/src
static_dir := $(lib.dir)/static
shared_dir := $(lib.dir)/shared

C_flag = -I $(inc.dir)

o:
	#tao file object
	gcc -c -fPIC $(scr.dir)/helloThanh.c -o $(obj.dir)/helloThanh.o -I $(inc.dir)
	gcc -c -fPIC $(scr.dir)/helloWorld.c -o $(obj.dir)/helloWorld.o -I $(inc.dir)
	gcc -c $(scr.dir)/main.c -o $(obj.dir)/main.o -I $(inc.dir)

lib:o
	#tao thu vien chia se .so
	gcc -shared $(obj.dir)/helloThanh.o $(obj.dir)/helloWorld.o -o $(shared_dir)/libshared.so
	
	#tao thu vien tinh .a
	ar rcs $(static_dir)/libstatic.a $(obj.dir)/helloThanh.o $(obj.dir)/helloWorld.o

all:o lib
	#lien ket
	#shared lib
	gcc  $(obj.dir)/main.o -L$(shared_dir) -lshared -o $(bin.dir)/sharedlibrary
	#static lib
	gcc  $(obj.dir)/main.o -L$(static_dir) -lstatic -o $(bin.dir)/staticlibrary

del:
	rm -rf $(obj.dir)/*.o
	rm -rf $(shared_dir)/*.so
	rm -rf $(static_dir)/*.a
	rm -rf $(bin.dir)/sharedlibrary
	rm -rf $(bin.dir)/staticlibrary
