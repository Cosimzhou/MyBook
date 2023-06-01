Configs
=======


# YAML

```
doc 1
...
%TAG !bar! !bar-types/
---
doc 2
```

# JSON


# XML


# TOML

```
[product]  # 生产环境的配置
sever.address = '192.168.1.100' # 层级风格

product.server.port = 80 # 层级展开风格
product.server.server = { context-path = '/context' }
product.server.tomcat.uri-encoding = 'utf-8'

[dev]  # 开发环境的配置
server = { address = '0.0.0.0', port = 8080 } # 行内风格
server.servlet.context-path = '/context-dev'
servlet.tomcat = { uri-encoding = 'utf-8' }
```

# Hocon

```
user = admin // 自动推断为字符串类型, 支持// 注释风格
password: 123456 # 支持 # 注释风格，键和值之间也可以使用冒号，123456推断为数字类型
password2 = "123456" # 显式申明为字符串类型，字符串只能使用双引号包裹

default {
  port: 80
  context-path: /context
  uri-encoding: utf-8
}

product { # 生产环境的配置
  server {  # 多级嵌套
    address: 192.168.1.100
    port: ${default.port} # 引用
  }
}

product.server.servlet { # 多级展开
  context-path: ${default.context-path}
}

product.server.tomcat {
  uri-encoding: ${default.uri-encoding}
}

dev {  # 开发环境的配置
  server {
    address: 0.0.0.0
    port: ${default.port}80 # 引用后可以"连接"上其他值
  }
}

dev.server.servlet {
  context-path: ${default.context-path}-dev # 没问题
}

dev.server.tomcat {
  uri-encoding: ${default.uri-encoding}
}

```

# CSON

# application.properties

```
com.company.version=1.0.1
com.company.project.package1.name=abcd
com.company.project.package2.name=abcd
#...
```

# INI
An out-dated old format configuration. Often used in some of the software based on the Microsoft platform.

