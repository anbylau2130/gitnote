select name,type_desc from sys.all_sql_modules  s  
inner join sys.all_objects o on s.object_id=o.object_id 
where definition like '%CMK_FN_GetUnitConvertRate%'  AND definition like '%FSALEUNITID%' AND name NOT  LIKE '%bak%'
ORDER by type_desc,name
