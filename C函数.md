# 数据结构：

## 哈希：`uthash`

### 第一步：包含头文件

```c
 #include "uthash.h"
```

### 第二步：自定义数据结构。

```c
//每个结构代表一个键-值对，并且，每个结构中要有一个UT_hash_handle成员。
struct HashTable {
int id; /* key */
int name[10];
UT_hash_handle hh; /* makes this structure hashable */
};
```

### 第三步：定义hash表指针。

```c
//这个指针为前面自定义数据结构的指针，并初始化为NULL。
struct HashTable *users = NULL; /* important! initialize to NULL */
/*
!!!
users在函数参数传递过程中要保证传递的是其本身
!!!
*/
```

### 第四步：进行一般的操作。

#### 增加：`HASH_ADD_INT (head, keyfield_name, item_ptr)`

```c
//key是int，可以使用 
HASH_ADD_INT();

//key是字符串，可以使用 
HASH_ADD_STR();

//key是指针,可以使用 
HASH_ADD_PTR();

//其它，可以使用 
HASH_ADD();
```

#### 查找：`HASH_FIND_INT (head, key_ptr, item_ptr)`

```c
//如果key是int，可以使用 
HASH_FIND_INT();

//key是字符串，可以使用 
HASH_FIND_STR();

//key是指针,可以使用 
HASH_FIND_PTR();

//其它，可以使用 
HASH_FIND();
```

#### 删除：`HASH_DEL (head, item_ptr)`

```c
//从哈希中删除项目
void delete_user(struct my_struct *user) {
    HASH_DEL(users, user);  /* user: pointer to deletee */
    free(user);             /* optional; it's up to you! */
}
/*
!!!
uthash从来没有释放你的结构,删除一个结构只是把它从哈希表-它没有。何时释放你的结构完全取决于你：uthash永远不会释放你的结构。例如，在使用宏时，将返回替换的输出参数，以便用户能够去分配它。
!!!
*/

//删除可以更改指头
//哈希表指头（最初指向添加到哈希中的第一个项目）可以更改为响应（即删除哈希表中的第一个项目）。

/*
立即删除:
如果您只想要删除所有项目，但不释放它们或进行任何每个元素的清理，您可以在单个操作中更高效地执行此操作：
*/
HASH_CLEAR(hh, users);
//之后，列表头（此处）将设置为。users=NULL;

/*
删除安全迭代
在上示示中，在循环的主体中删除和释放不安全（因为每次循环反复时都会取消引用）。这很容易正确重写（通过在释放前将指针复制到临时变量），但它经常出现，包括删除安全迭代宏。它扩展到循环头。下面是如何使用它重写最后一个例子：sss->hh.nextsHASH_ITERfor
*/

struct my_struct *s, *tmp;
HASH_ITER(hh, users, s, tmp) {
    printf("user id %d: name %s\n", s->id, s->name);
    /* ... it is safe to delete and free s here */
}
```

#### 替换：`HASH_REPLACE_INT (head, keyfield_name, item_ptr, replaced_item_ptr)`

```c
//如果key是int，可以使用 
HASH_REPLACE_INT();

//key是字符串，可以使用 
HASH_REPLACE_STR();

//key是指针,可以使用 
HASH_REPLACE_PTR();

//其它，可以使用 
HASH_REPLACE();
```

#### 计数：`HASH_COUNT (head)`

```c
unsigned int num_users;
num_users = HASH_COUNT(users);
printf("there are %u users\n", num_users);
```

#### 排序：`HASH_SORT (head, cmp)`

```c
int sort_function(void *a, void *b) {
  /* compare a to b (cast a and b appropriately)
   * return (int) -1 if (a < b)
   * return (int)  0 if (a == b)
   * return (int)  1 if (a > b)
   */
}

int name_sort(struct my_struct *a, struct my_struct *b) {
    return strcmp(a->name, b->name);
}

int id_sort(struct my_struct *a, struct my_struct *b) {
    return (a->id - b->id);
}

void sort_by_name() {
    HASH_SORT(users, name_sort);
}

void sort_by_id() {
    HASH_SORT(users, id_sort);
}
```

#### 遍历哈希表中的所有项目

```c
void print_users() {
    struct my_struct *s;

    for(s=users; s != NULL; s=s->hh.next) {
        printf("user id %d: name %s\n", s->id, s->name);
    }
}
/*
还有一个 hh.prev 指针，可用于从任何已知项开始向后迭代哈希。
由于 hh.prev 和 hh.next 字段的缘故，可以在哈希中向前和向后迭代。
可以通过重复跟随这些指针来访问哈希中的所有项目，因此哈希也是双链表。
*/
```

#### 一般宏：

```c
HASH_ADD (hh_name, head, keyfield_name, key_len, item_ptr);

HASH_ADD_BYHASHVALUE (hh_name, head, keyfield_name, key_len, hashv, item_ptr);

HASH_ADD_KEYPTR (hh_name, head, key_ptr, key_len, item_ptr);

HASH_ADD_KEYPTR_BYHASHVALUE (hh_name, head, key_ptr, key_len, hashv, item_ptr);

HASH_ADD_INORDER (hh_name, head, keyfield_name, key_len, item_ptr, cmp);

HASH_ADD_BYHASHVALUE_INORDER (hh_name, head, keyfield_name, key_len, hashv, item_ptr, cmp);

HASH_ADD_KEYPTR_INORDER (hh_name, head, key_ptr, key_len, item_ptr, cmp);

HASH_ADD_KEYPTR_BYHASHVALUE_INORDER (hh_name, head, key_ptr, key_len, hashv, item_ptr, cmp);

HASH_REPLACE (hh_name, head, keyfield_name, key_len, item_ptr, replaced_item_ptr);

HASH_REPLACE_BYHASHVALUE (hh_name, head, keyfield_name, key_len, hashv, item_ptr, replaced_item_ptr);

HASH_REPLACE_INORDER (hh_name, head, keyfield_name, key_len, item_ptr, replaced_item_ptr, cmp);

HASH_REPLACE_BYHASHVALUE_INORDER (hh_name, head, keyfield_name, key_len, hashv, item_ptr, replaced_item_ptr, cmp);

HASH_FIND (hh_name, head, key_ptr, key_len, item_ptr);

HASH_FIND_BYHASHVALUE (hh_name, head, key_ptr, key_len, hashv, item_ptr);

HASH_DELETE (hh_name, head, item_ptr);

HASH_VALUE (key_ptr, key_len, hashv);

HASH_SRT (hh_name, head, cmp);

HASH_CNT (hh_name, head);

HASH_CLEAR (hh_name, head);

HASH_SELECT (dst_hh_name, dst_head, src_hh_name, src_head, condition);

HASH_ITER (hh_name, head, item_ptr, tmp_item_ptr);

HASH_OVERHEAD (hh_name, head);
```

