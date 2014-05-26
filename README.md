tornado
=======

Python Tornado Freamwork

####Download
http://www.tornadoweb.org/en/stable/#

####Install
0. tar xvzf tornado-3.2.1.tar.gz
0. cd tornado-3.2.1
0. python setup.py build
0. sudo python setup.py install

####Helloworld
Create helloworld.py
    
    !/usr/bin/env python
    
    import tornado.httpserver
    import tornado.ioloop
    import tornado.options
    import tornado.web
    
    from tornado.options import define, options
    
    define("port", default=8888, help="run on the given port", type=int)
    
    
    class MainHandler(tornado.web.RequestHandler):
        def get(self):
            self.write("Hello, world")
    
    
    def main():
        tornado.options.parse_command_line()
        application = tornado.web.Application([
            (r"/", MainHandler),
        ])
        http_server = tornado.httpserver.HTTPServer(application)
        http_server.listen(options.port)
        tornado.ioloop.IOLoop.instance().start()
    
    
    if __name__ == "__main__":
        main()

####Test run
0. helloworld.py
0. Access to "localhost:8888"