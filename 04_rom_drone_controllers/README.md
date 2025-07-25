#### Compile Process File Location
```
PX4-Autopilot/src/ # သူက flight stack ရဲ့ အဓိက cpp ရှိတဲ့နေရာ
PX4-Autopilot/src/modules/simulation/ # သူက simulation interface gz_bridge တို့လိုကောင်တွေရှိတဲ့နေရာ

PX4-Autopilot/Tools/simulation/gz/ # သူက submodule တစ်ခုဖြစ်ပြီး Gazebo models နဲ့ world files တွေပါတယ်။
PX4-Autopilot/Tools/simulation/gz/models/x500 # သူထဲက model.sdf က robot model ပေါ့
PX4-Autopilot/Tools/simulation/gz/worlds # သူကတော့ world  ဖိုင်တွေပေါ့။ ပုံမှန် gz_x500 ဆိုရင် default.world ကို ဖွင့်မှာ


PX4-Autopilot/Tools/simulation/gz/src # သူ့ထဲမှာတော့ gazebo အတွက် plugin lib တွေပါ။

929d55e8832fcd1a1432d2ae1b36601455ec7ed7