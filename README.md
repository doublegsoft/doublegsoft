doublegsoft
===========

## Modelbase

Modelbase是设计用来描述领域模型的一种DSL语言，简单易用，容易理解并且上手。示例如下：

```

@name(label='联系人基本信息', singular='contact', plural='contacts')
@persistence(name='tn_pim_cont', revision='tr_pim_cont')
@entity
contact<
  
  @persistence(name='contid')
  @name(label='联系人标识')
  id!!: &person(id),

  @persistence(name='contnm')
  @name(label='联系人标识')
  name: string(128),

  @persistence(name='pos')
  @name(label='职位')
  position: string(64),

  @persistence(name='mob')
  @name(label='手机号码')
  mobile: string(128),

  @persistence(name='eml')
  @name(label='电子邮箱')
  email: string(128),

  @persistence(name='employorgid')
  @name(label='雇佣公司标识')
  @reference(value='id', name='employed_organization')
  employed_organization_id: string(64),

  @persistence(name='employorgtyp')
  @name(label='雇佣公司类型')
  @reference(value='type', name='employed_organization')
  employed_organization_type: string(64),

  @persistence(name='nt')
  @name(label='说明')
  note: string(1000),
  
  @persistence(name='modid', text='修改者标识')
  @reference(value='id', name='modifier')
  modifier_id: string(64),

  @persistence(name='modtyp', text='修改者类型')
  @reference(value='type', name='modifier')
  modifier_type: string(64),

  @persistence(name='sta', text='系统状态')
  state: state,
  
  @persistence(name='lmt', text='最近修改时间')
  last_modified_time: now
>
```

我们的思路是通过

```
model + best practice = source code
```

Modelbase Studio界面，通过此软件，我们把model转换成那个java和其他语言形式的代码，把java代码编辑打包发布到maven库中，其他脚本形式的代码则发布到git库中。

![](asset/image/modelbase-studio.png)

Modelbase给团队开发带来的增益流程

![](asset/image/management.gif)

## Guidbase