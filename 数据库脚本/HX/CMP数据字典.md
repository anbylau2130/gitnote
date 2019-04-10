``` sql
SELECT 
a.sUpdVerNo,
a.IsAllRecord as "全部记录",
a.IsEditToInsert as "修改转插入",
a.IsPurview as "权限",
a.IsReadOnly as "只读",
a.IsUpdateFlag as "修改标志",
a.dDate as "日期",
a.eMultiType as "重复类型",
a.eType as "数据|对象类型",
a.mDoc as "流数据",
a.sAfterPostBuzRule as "写入后业务规则",
a.sBeforePostBuzRule as "写入前业务规则",
a.sConnName as "连接标志",
a.sDataObjID as "数据|对象号",
a.sDataObjName as "数据|字典名称",
a.sDatasetName as "数据|物理表名",
a.sDefaultOrder as "默认查询顺序",
a.sExtParams as "用户扩展参数",
a.sFixedSearch as "固定查询条件",
a.sLockStr as "锁的语句",
a.sMainKeyFields as "主键字段表",
a.sMultiFields as "重复检查字段",
a.sMultiMsg as "重复提示信息",
a.sPageCaptions as "分页标题表",
a.sSaveProcName as "保存储存过程名",
a.sSubSystem as "数据|子系统",
a.sUpdVerNo as "数据字典版本",
a.sVerNo as "版本",
b.IsActive as "可用",
b.IsAutoOrder as "自动序号",
b.IsCalc as "计算属性",
b.IsCtrlDataCenter as "是否控制数据中心权限",
b.IsDispSele as "显示选项",
b.IsEditLimit as "编辑受限",
b.IsEditable as "编辑",
b.IsMainQrySele as "查询选项",
b.IsOnlyOne as "受限明细",
b.IsPrimaryKey as "主键",
b.IsPurview as "权限",
b.IsRefMuilt as "参照|多选",
b.IsRefQrySele as "参照|查询选项",
b.IsRefable as "参照|可用",
b.IsRequired as "必填",
b.IsStrictRef as "参照|严格",
b.IsZeroSpace as "零空",
b.Precision as "精度",
b.eIDType as "ID属性类型",
b.eProcParaType as "参数类型",
b.ePropType as "属性类型",
b.eRefType as "参照|类型",
b.eStatType as "统计类型",
b.eViewable as "显示",
b.nDataWidth as "数据尺寸",
b.nDecimal as "小数位数",
b.nDispIndex as "显示|序号",
b.nDispWidth as "显示|编辑宽度",
b.nGridWidth as "显示|网格宽度",
b.nLabelWidth as "显示|标签宽度",
b.nPageNo as "显示|页号",
b.nPropID as "序号",
b.sBuzType as "业务类型",
b.sCaption as "显示|标题",
b.sCheckRule as "检查规则",
b.sDataObjID as "数据对象号",
b.sDataRightCode as "数据权编码",
b.sDatasetName as "数据集名称",
b.sDefaultValue as "默认值",
b.sDescription as "描述",
b.sEditRule as "编辑规则",
b.sExtParams as "用户扩展参数",
b.sFieldItem as "字段项目",
b.sFieldName as "字段名称",
b.sFormatString as "显示格式",
b.sHint as "提示信息",
b.sLargTextFlag as "大文本标记",
b.sMatch as "参照|通配符",
b.sPropName as "属性名称",
b.sRealm as "域",
b.sRefDataObj as "参照|对象",
b.sRefDyanSearch as "参照|动态条件",
b.sRefField as "参照|关联字段",
b.sRefNameField as "参照|关联名称",
b.sRefQuery as "参照|查询条件",
b.sRefRegForm as "参照|注册窗体",
b.sRefSearch as "参照|条件",
b.sRefSelCondition as "参照|选择条件",
b.sRefSeparator as "参照|分隔符",
b.sSetRule as "赋值规则",
b.sVerNo as "版本",
b.sViewRule as "显示规则"

FROM tFraDataObj a
LEFT JOIN tFraDataObjProp b ON a.sdataobjid =b.sdataobjid
WHERE --a.sDatasetName='tFraDataObjProp' and 
a.sUpdVerNo=(SELECT max(sUpdVerNo) FROM tFraDataObj WHERE sDatasetName=a.sDatasetName)
ORDER BY a.sDatasetName,b.npropid
 ```
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
SELECT
'b.'||b.sfieldname||' as "'||b.scaption||'",' ,
a.*
FROM tFraDataObj a
LEFT JOIN tFraDataObjProp b ON a.sdataobjid =b.sdataobjid
WHERE a.sDatasetName='tFraDataObjProp' AND a.sUpdVerNo='0003' 