---
title: "窗口计数（Windows程序设计）"
tags: ""
---
# 前言

  我总要写点东西吧，不然感觉难道不是很无趣？（~~其实是没什么东西好写~~）**那就记录一下Windows程序设计吧**(｀・ω・´)

# 问题描述

-   主窗口启动后产生6个从属窗口，整齐排成3行，大小均为（200,80）；
-   点击按钮可以创建新窗口，也可关闭一个或多个子窗口;
-   主窗口跟踪从属窗口的状态并显示实时窗口数量；
-   每个窗口均无最大化最小化按钮；
-   启动后自动产生6个子窗体,动态增加2个窗体，再关掉2个窗体后，主窗口自动更新窗口数量；

     ![要求](https://images.cnblogs.com/cnblogs_com/xxhao/1658666/o_2003031344421.png)

# 解决思路

### 设置两个计数器，一个为现存子窗口数量counter，一个为子窗口的id,total

### 利用子窗口的id 和Height，Top，Left控制子窗口的位置

### 完整代码如下

    public Form2()
            {
                InitializeComponent();
                Height = 300; Width = 500;
            }
            int counter = 0;
            int total = 0;
            private void Form2_Load(object sender, EventArgs e)
            {
                for (int i = 0; i < 6; i++) AddFrorm();  
                Text = "当前拥有的子窗口数为" + counter;  
            }

            private void button1_Click(object sender, EventArgs e)
            {
                AddFrorm();
                Text = "当前拥有的子窗口数为" + counter;
            }

            private void AddFrorm()
            {
                Form form = new Form();
                form.Height = 80;
                form.Width = 200;
                form.FormBorderStyle = FormBorderStyle.FixedToolWindow;
                form.Text = "子窗口" + ++total; counter++;
                form.FormClosing += Form_FormClosing;
                form.StartPosition = FormStartPosition.Manual;
                form.Top = (total-1) / 3 * 100+Height+Top;
                form.Left = (total-1) % 3 * 250 + Left;
                form.Show();  
            }

            private void Form_FormClosing(object sender, FormClosingEventArgs e)
            {
               Text = "当前拥有的子窗口数为" + --counter;
            }

# 后记

> 体验不是很好，可能是没写习惯，真香警告？ = v =
