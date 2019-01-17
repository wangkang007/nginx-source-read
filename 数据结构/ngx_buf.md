## ngxbuf
```c
struct ngx_buf_s {
    // pos指向的是这段数据在内存中的开始位置
    u_char          *pos;
    u_char          *last;
    // file_pos指向的是这段数据在文件中的开始位置
    off_t            file_pos;
    off_t            file_last;
// 如果ngx_buf_t 缓冲区用于内存，start则指向这段内存的起始地址
    u_char          *start;         /* start of buffer */
    u_char          *end;           /* end of buffer */
    ngx_buf_tag_t    tag;
    //具体的文件指针
    ngx_file_t      *file;
    ngx_buf_t       *shadow;


    /* the buf's content could be changed */
    //标志内存是可以被修改的
    unsigned         temporary:1;

    /*
     * the buf's content is in a memory cache or in a read only memory
     * and must not be changed
     */
    // buf内容是在内存上的
    unsigned         memory:1;

    /* the buf's content is mmap()ed and must not be changed */
    //标志内存中的数据是通过mmap内存映射文件来的
    unsigned         mmap:1;
    //  标志这些内存是否可以被回收
    unsigned         recycled:1;
    // 当buf所包含的内容在文件中时，file字段指向对应的文件对象上去
    unsigned         in_file:1;
    unsigned         flush:1;
    //这块内存的操作方式，是异步还是同步
    unsigned         sync:1;
    //此字段为1表明这是最后一个buf
    unsigned         last_buf:1;
    //在当前的chain里面，此buf是最后一个
    unsigned         last_in_chain:1;

    unsigned         last_shadow:1;
    //由于内存使用的限制，有时候一些buf的内容需要被写到磁盘上的临时文件中去
    unsigned         temp_file:1;

    /* STUB */ int   num;
};

```