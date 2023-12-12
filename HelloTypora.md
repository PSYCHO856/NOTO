Typora软件和Markdown语

![image-20211201191256453](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211201191256453.png)



\\192.168.110.226\阵列仿真安装包\阵列水利实验仿真软件

FFF8D1



editor扩展 LTgame LTEditorWindow

excel questionconfig转为json 自动生成模板类



configInfo ReadConfig读取json



```
QuestionConfigInfo
static Dictionary<string, QuestionConfig> datas
存储数据

```

***\*我方承诺\*******\*每个实验\*******\*都\*******\*含有文字介绍及实验仪器介绍\*******\*。\****

***\*我方承诺\*******\*每个实验模块学生交互\*******\*都\*******\*不少于10步\*******\*。\****



1在天平上称环刀质量m1 放环刀

2电子秤点击

3

4在环刀内壁涂一薄层凡士林

5将环刀刃口向下放在土样上

6环刀垂直下压

7边压边削，直至土样上端伸出环刀为止

8将环刀两端余土削去修平，擦净环刀外壁。

9将取好土样的环刀放在天平上称量

10电子秤点击



ui

~~左侧及时提示教学步骤~~

~~点击器材显示ui~~ 

​	~~第一次在上方显示说明ui~~

​    ~~显示进行操作的按钮~~

学生登录

导出实验报告

答题检测

移动

器具移动动画

​	获取两器具位置 向上移动 相对移动 向下移动

旋转 环刀旋转180度

刮土刀



顶部ui 操作说明



数据结构steps

存储每一步的描述 要用到的器具 

器具ui显示

第一次点击器具的介绍

当前步骤完成的判定







住房300+280

杭州临安银行



镜头跟随lateupdate 放大缩小

动画平滑

实验室调亮

阻止点击到ui下层





15号

打开ui时禁用场景操作

实验4



桌子换颜色

透明材质 ~~布料~~

pbr反光



土壤操作动画

设备认知 截屏

metallic shader maintex白色





全部清楚









时间上觉得是实验用不了多少时间

要求上又要精益求精做的比其他的都好

然后还有一堆参考视频之外的需求内容



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
