## 修改了使用etcd存储的域名解析方式，不采用递归方式获取etcd记录

### 测试用例
etcdctl put /skydns/com/demo/test/ '{"host":"1.1.1.1"}'
etcdctl put /skydns/com/demo/test/a/ '{"host":"2.2.2.2"}'
etcdctl put /skydns/com/demo/test/a/b/ '{"host":"3.3.3.3"}'

dig +short test.demo.com @localhost
1.1.1.1

dig +short a.test.demo.com @localhost
2.2.2.2

dig +short b.a.test.demo.com @localhost
3.3.3.3
