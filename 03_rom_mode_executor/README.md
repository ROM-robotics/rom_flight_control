Class                                               arm         takeoff        land              disarm
MOdeBaseExecutor--> FlightWithLocalVelocity        မရ             ရ             ရ                ရ ပေမဲ့ error ရှိ ( နောက်တခါ loop မရ )
MOdeBaseExecutor--> FlightWithVelocity             မရ             ရ             ရ                ရ ပေမဲ့ error ရှိ ( နောက်တခါ loop မရ )
executor မသုံးရင်  --> FlightWithVelocity             မရ             မရ            မရသေး            မရ ပေမဲ့ error မရှိပဲ နောက်တကြိမ် loop ခိုင်းလို့ရတယ်။

``` 
ခုတော့ takeoff, landing များကို မဖြေရှင်းသေးဘဲ Autonomous ဘက်သွားမည်။
```