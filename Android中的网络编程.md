# 基础知识
- 使用C#进行WebService服务器端开发
- 使用JAVA进行WebService客户机端开发
##  WebService
目的： 用于andorid app与远端服务器交互

Web Service基础：
- Web Service的数据格式XML
- 面向服务的架构SOA
- 简单对象访问协议：SOAP（HTTP底层就是SOAP协议）
- 服务描述：WSDL（参数，操作，返回值）
- 网上自动查找WebService：UDDI

### 使用方法
[http://ws.webxml.com.cn/](http://ws.webxml.com.cn/)  是一个提供WebService服务网站，调用相应的方法会返回对应的xml文件。
![image.png](https://i.loli.net/2020/05/02/hrPeRFH93wgxIfz.png)
也可以通过[iis](https://jingyan.baidu.com/article/6079ad0eb37aac28fe86db6a.html)发布c#的Web Service服务 

下面是andorid内部获取Web Service的数据的方法

```
        String nameSpace="http://WebXml.com.cn/";//命名空间
        String methodName="getRegionProvince";//调用方法名称
        String soapAction="http://WebXml.com.cn/getRegionProvince";//SOAP Action上面两者结合
        String endPoint="http://ws.webxml.com.cn/WebServices/WeatherWS.asmx";//提供webService的地址

        SoapObject rpc=new SoapObject(nameSpace,methodName);

        //加入参数
        //rpc.addProperty("id",id)
        SoapSerializationEnvelope envelope=new SoapSerializationEnvelope(SoapEnvelope.VER11);

        envelope.bodyOut=rpc;
        envelope.dotNet=true;              //设置是否调用于doNet开发的WebService
        envelope.setOutputSoapObject(rpc); //等价于envelope.bodyOut=rpc

        HttpTransportSE transport=new HttpTransportSE(endPoint);
        try {
            transport.call(soapAction,envelope);
        }catch (Exception e) {
            e.printStackTrace();
        }

        SoapObject object=(SoapObject) envelope.bodyIn;//获取返回的数据
        result=object.getProperty(0).toString();//获取返回的结果

        //线程传输数据
        Message mm=Message.obtain();
        mm.what=1;
        handler.sendMessage(mm);
```
上述操作的配套线程代码
```
//线程类
class TTT1 extends Thread {
        @Override
        public void run() {
            GetNew();
        }
    }

//线程实例
TTT work=new TTT();
 work.start();

//提到数据之后的操作
private Handler handler = new Handler() {
        public void handleMessage(Message msg) {
            switch (msg.what) {
                case 1:
                   //具体操作 result
                    break;
            }
        }
    };
```
在c#当中访问当地数据库方法
```
 //数据库的信息
            string connStr = "server =.;database=News;uid=sa;pwd=123456";
            try
            {
                SqlConnection conn = new SqlConnection(connStr);
                conn.Open();
                conn.Close();
                return true;
            }
            catch
            {
                return false;
            }
```

查询操作

```
       //数据库的信息
            string connStr = "server =.;database=News;uid=sa;pwd=123456";
           
            try
            {
                string sqlStr = "select * from News";

                DataSet ds = new DataSet();

                SqlDataAdapter da = new SqlDataAdapter(sqlStr, new SqlConnection(connStr));

                da.Fill(ds);

                return ds;
            }
            catch
            {
                return null;
            }
```
其实用EF框架也挺好的

### 具体实例
 请看[这里](https://github.com/taoyeh/Android/tree/Internet)