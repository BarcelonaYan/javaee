#server.py
#从wsgiref模块导入
from wsgiref.simple_server import make_server

#创建一个服务器，IP地址为空，端口是8080，处理函数是application：
httpd = make_server('',8080,application)
print("Serving HTTP on port 8080")

#开始监听HTTP请求：
httpd.serve_forever()

def application(environ,start_response):
    p=environ['PATH_INFO'][1:]

    #判断静态还是动态资源
    if ".html" in p:
        BASE_DIR=os.path.dirname(__file__)
        path=os.path.join(BASE_DIR, p)

        if os.path.exists(path):
            f=open(path,'r')
            start_response('200 OK',[('Content-Type','text/html')])
            body=f.read()
            f.close()
            return [body.encode('utf-8')]
        else:
            start_response('404 not found',[('Content-Type','text/html')])
            body='<h1>%s</h1>'%path
            return [body.encode('utf-8')]
    else:
        start_response('200 OK',[('Content-Type','text/html')])
        body='<h1>hello %s!</h1>' % (environ['PATH_INFO'][1:])
        return[body.encode('utf-8')]


            
          
