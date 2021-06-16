# 需求
在写android过程中常常会需要使用到适配器的地方，比如下图中的规则类似list需求。

![image.png](https://i.loli.net/2020/05/05/I7NApFrYjyqMUXv.png)
# 方法
## 复杂写法

- 首先要建立一个model用于暂时存放数据。建立一个xml外观文件，用于页面布局。
- 之后要建一个adpter类，用于把数据与外观文件绑定

```
public class NewsAdpter  extends ArrayAdapter<News> {
    private  int rid;
    //构造函数
    public  NewsAdpter(Context context, int resource, List<News> objects){
       super(context,resource,objects);
        rid=resource;
    }
    // data是数据，把它放到对应的xml文件当中
    @NonNull
    @Override
    public View getView(int position, @Nullable View convertView, @NonNull ViewGroup parent) {
        News data=getItem(position);  //获取position项的News实例
        View view= LayoutInflater.from(getContext()).inflate(rid,parent,false);
        TextView newid=view.findViewById(R.id.newid);
        TextView title=view.findViewById(R.id.title);
        TextView content=view.findViewById(R.id.content);
        TextView ndata=view.findViewById(R.id.datatime);
        newid.setText(data.nid+"");
        title.setText(data.title);
        content.setText("\u3000\u3000"+data.content);
        ndata.setText(data.data);
        return view;
    }
}
```
- 声明绑定

```
        //R.layout.news_layout是xml文件，nn是model数据类型
        //public static List<News> nn = new ArrayList<News>()
        NewsAdpter adpter=new NewsAdpter(this,R.layout.news_layout,nn);
        news_list.setAdapter(adpter);
```