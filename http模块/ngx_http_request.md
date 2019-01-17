
##整体流程
ngx_http_init_connection->ngx_http_wait_request_handler->ngx_http_process_request_line->ngx_http_process_request_headers->ngx_http_process_request_header->ngx_http_process_request->ngx_http_handler(未读)->ngx_http_core_run_phases->checker阶段
##ngx_http_init_connection
负责http request的初始化操作

##响应
ngx_http_write_filter 写结果