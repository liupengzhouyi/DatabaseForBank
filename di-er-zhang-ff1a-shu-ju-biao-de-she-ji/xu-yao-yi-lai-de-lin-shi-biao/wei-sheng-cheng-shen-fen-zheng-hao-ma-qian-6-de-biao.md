# 身份证号码前6位信息表

## 数据表信息

| 字段名称 | 数据类型 | 是否主键 | 是否自增 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| number | int | 是 | 是 | 编号 |
| address\_number | varchar\(7\) | 否 | 否 | 前6位编号 |
| address\_name | VARCHAR\(20\) | 否 | 否 | 编号所代表的地址 |

## 创建数据表的代码

```
-- 创建一个地址表
CREATE TABLE tb_temp_address_table
(
  -- 编号
  number INT PRIMARY KEY IDENTITY (1, 1) ,
  -- 地址编号
  address_number VARCHAR(7) NOT NULL ,
  -- 地址名称
  address_name VARCHAR(20) NOT NULL
);
```
## 导入的数据


```

INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110000', '北京市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110100', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110101', '东城区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110102', '西城区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110103', '崇文区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110104', '宣武区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110105', '朝阳区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110106', '丰台区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110107', '石景山区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110108', '海淀区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110109', '门头沟区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110111', '房山区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110112', '通州区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110113', '顺义区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110114', '昌平区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110115', '大兴区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110116', '怀柔区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110117', '平谷区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110200', '县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110228', '密云县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('110229', '延庆县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120000', '天津市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120100', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120101', '和平区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120102', '河东区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120103', '河西区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120104', '南开区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120105', '河北区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120106', '红桥区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120107', '塘沽区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120108', '汉沽区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120109', '大港区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120110', '东丽区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120111', '西青区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120112', '津南区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120113', '北辰区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120114', '武清区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120115', '宝坻区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120200', '县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120221', '宁河县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120223', '静海县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('120225', '蓟县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130000', '河北省');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130100', '石家庄市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130101', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130102', '长安区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130103', '桥东区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130104', '桥西区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130105', '新华区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130107', '井陉矿区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130108', '裕华区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130121', '井陉县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130123', '正定县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130124', '栾城县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130125', '行唐县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130126', '灵寿县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130127', '高邑县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130128', '深泽县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130129', '赞皇县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130130', '无极县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130131', '平山县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130132', '元氏县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130133', '赵县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130181', '辛集市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130182', '藁城市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130183', '晋州市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130184', '新乐市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130185', '鹿泉市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130200', '唐山市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130201', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130202', '路南区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130203', '路北区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130204', '古冶区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130205', '开平区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130207', '丰南区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130208', '丰润区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130223', '滦县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130224', '滦南县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130225', '乐亭县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130227', '迁西县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130229', '玉田县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130230', '唐海县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130281', '遵化市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130283', '迁安市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130300', '秦皇岛市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130301', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130302', '海港区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130303', '山海关区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130304', '北戴河区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130321', '青龙满族自治县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130322', '昌黎县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130323', '抚宁县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130324', '卢龙县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130400', '邯郸市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130401', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130402', '邯山区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130403', '丛台区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130404', '复兴区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130406', '峰峰矿区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130421', '邯郸县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130423', '临漳县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130424', '成安县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130425', '大名县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130426', '涉县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130427', '磁县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130428', '肥乡县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130429', '永年县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130430', '邱县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130431', '鸡泽县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130432', '广平县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130433', '馆陶县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130434', '魏县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130435', '曲周县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130481', '武安市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130500', '邢台市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130501', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130502', '桥东区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130503', '桥西区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130521', '邢台县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130522', '临城县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130523', '内丘县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130524', '柏乡县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130525', '隆尧县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130526', '任县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130527', '南和县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130528', '宁晋县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130529', '巨鹿县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130530', '新河县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130531', '广宗县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130532', '平乡县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130533', '威县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130534', '清河县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130535', '临西县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130581', '南宫市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130582', '沙河市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130600', '保定市');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130601', '市辖区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130602', '新市区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130603', '北市区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130604', '南市区');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130621', '满城县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130622', '清苑县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130623', '涞水县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130624', '阜平县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130625', '徐水县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130626', '定兴县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130627', '唐县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130628', '高阳县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130629', '容城县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130630', '涞源县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130631', '望都县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130632', '安新县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130634', '曲阳县');
INSERT INTO tb_temp_address_table(address_number, address_name) VALUES ('130635', '蠡县');
```




