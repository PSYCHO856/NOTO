Typora软件和Markdown语

![image-20211201191256453](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211201191256453.png)

D:\OthersProjects\软件加密

服务器新地址：\\192.168.110.222



\\192.168.110.223\阵列仿真安装包\阵列水利实验仿真软件

\\192.168.110.226\阵列仿真安装包\阵列水利实验仿真软件

\\192.168.110.226\开发部备份\于展翔

D:\githubrepository\NormalTemplate

<input type="hidden" id="command" value="arraygdsyshjjc://Command?id=0&amp;type=0&amp;host=http://192.168.110.160:82&amp;courseid=9&amp;userName=test1&amp;token=9ef70f448920e20b55ae4ffc5e832fa0">

```
Debug.Log(" " + );
```

```
btnKnow =  UtilityTool.FindChild<Button>(transform, "btnKnow");
btnKnow.onClick.AddListener(() =>
{
    
});
```

蔬菜技能大赛

oL/Qh6Hmwk5fzIYRdoYHnk9/jm2C3N2XqmDJRjFmGRxrFGw+/Vf6UQ==

蔬菜栽培

JOHzpFUAvQmfvs6ljwXIjj7Z2L/m0a6vQVDBelj+kPv1PVwF3zKduA==

任务：

只能灌溉 评分标准

蔬菜贮藏

地质灾害

```
MainMenuPanel HaspLock.Instance?.LoginHasp();
```





项目汇总

地质灾害调查与评价虚拟仿真软件（地质灾害调查与评价虚拟仿真实训系统）

阵列水利实验仿真软件（土力学教学实验虚拟仿真软件）

水利工程电子沙盘虚拟仿真软件

水利枢纽布置VR系统PC

阵列水环境监测虚拟仿真软件

智能灌溉系统运行与维护虚拟仿真实训



项目汇总

阵列蔬菜栽培技术虚拟仿真软件

蔬菜嫁接技能大赛

阵列园艺产品贮藏与加工仿真软件







是不是像别人一样带上面具加入假面舞会

要有经历，但不要让人看出来

交朋友和自己 要开朗，脸上无风霜，眼睛有故事



无论是看不见的手还是看得见的手 都不是我们能碰得到的 所以活得很自由 可以说是躺平了 能融入现在青年的主流价值观我觉得还挺荣幸的

刚开始我妈还和我理论，我现在摆烂了 承认了 不过我觉得她也挺躺的，信什么佛教





今天发现了书里那些美好的背面真实的苦难 极少的人真的活在现实里

![image-20231128093307174](C:\Users\30998\AppData\Roaming\Typora\typora-user-images\image-20231128093307174.png)





informa

editor扩展 LTgame LTEditorWindow

excel questionconfig转为json 自动生成模板类



configInfo ReadConfig读取json



顶部ui 操作说明



数据结构steps

存储每一步的描述 要用到的器具 

器具ui显示

第一次点击器具的介绍

当前步骤完成的判定







住房300+280

杭州临安银行







```
Tags { "RenderType"="Opaque" }
LOD 100

Pass
{
    CGPROGRAM
    #pragma vertex vert
    #pragma fragment frag
    #pragma multi_compile _ _DISSOLVEEFFECT_ON
    //注意，这里要一定要以_ON结尾
 

    #include "UnityCG.cginc"

    struct appdata
    {
        float4 vertex : POSITION;
        float2 uv : TEXCOORD0;
    };

    struct v2f
    {
        float2 uv : TEXCOORD0;
        float4 vertex : SV_POSITION;
    };

    sampler2D _MainTex;
    float4 _MainTex_ST;
    sampler2D _DissolveTex;
    float4 _DissolveTex_ST;
    float _Clip;
    float4 _RampColor;
    float _DissolveEffect;


    v2f vert (appdata v)
    {
        v2f o;
        o.vertex = UnityObjectToClipPos(v.vertex);
        o.uv = TRANSFORM_TEX(v.uv, _MainTex);
        UNITY_TRANSFER_FOG(o,o.vertex);
        return o;
    }

    fixed4 frag (v2f i) : SV_Target
    {
        // sample the texture
        fixed4 col = tex2D(_MainTex, i.uv);         
    #if _DISSOLVEEFFECT_ON
        i.uv = TRANSFORM_TEX(i.uv,_DissolveTex);
        //i.uv = i.uv * _DissolveTex_ST.xy + _DissolveTex_ST.zw; 上面那句代码相当于这局代码的简写.
        fixed4 dissolveCol = tex2D(_DissolveTex,i.uv);        
        clip(dissolveCol.r - _Clip);

        fixed maxEdge = _Clip + 0.1;            
        if(dissolveCol.r < maxEdge)
        {
            col += _RampColor * smoothstep(_Clip,maxEdge,dissolveCol.r);
        }
    #endif
    
        return col;
    }
    ENDCG
}
```

```
Unlit/NewUnlitShader
```

我活在社会里是想去改变他，你活在社会里是因为什么都不懂并且是日子人，

我们之间差太多了





永远的阵痛 永远的时代泪谷



犯了错（诞生而获得的原罪

身上烙了印

哈哈 这不是我们圣经的典吗 下次使用必须表明出处哈



拥有说话的权利 然后存在就好了



据说人一段时间不觉得自己是傻x就会变成僵尸

```
思考的滞后性让它本身带有了消极能量 所以我们一起跳舞吧
```

```
咕噜咕噜的翻滚着
```

上一世我优柔寡断走到死胡同里绝望的拥抱信仰，这一次我握紧武器绝不重蹈覆辙！

我的爆炎就是太阳！

如果我们真的掌握了魔法，那他就能发挥作用
