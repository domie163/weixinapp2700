<template>
  <div class="addEdit-block">
    <el-form
      class="detail-form-content"
      ref="ruleForm"
      :model="ruleForm"
      :rules="rules"
      label-width="80px"
	  :style="{backgroundColor:addEditForm.addEditBoxColor}"
    >
      <el-row >
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="学号" prop="xuehao">
          <el-input v-model="ruleForm.xuehao" 
              placeholder="学号" clearable  :readonly="ro.xuehao"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="学号" prop="xuehao">
              <el-input v-model="ruleForm.xuehao" 
                placeholder="学号" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="姓名" prop="xingming">
          <el-input v-model="ruleForm.xingming" 
              placeholder="姓名" clearable  :readonly="ro.xingming"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="姓名" prop="xingming">
              <el-input v-model="ruleForm.xingming" 
                placeholder="姓名" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="24">  
        <el-form-item class="upload" v-if="type!='info' && !ro.zhaopian" label="照片" prop="zhaopian">
          <file-upload
          tip="点击上传照片"
          action="file/upload"
          :limit="3"
          :multiple="true"
          :fileUrls="ruleForm.zhaopian?ruleForm.zhaopian:''"
          @change="zhaopianUploadChange"
          ></file-upload>
        </el-form-item>
        <div v-else>
          <el-form-item v-if="ruleForm.zhaopian" label="照片" prop="zhaopian">
            <img style="margin-right:20px;" v-bind:key="index" v-for="(item,index) in ruleForm.zhaopian.split(',')" :src="$base.url+item" width="100" height="100">
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="性别" prop="xingbie">
          <el-input v-model="ruleForm.xingbie" 
              placeholder="性别" clearable  :readonly="ro.xingbie"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="性别" prop="xingbie">
              <el-input v-model="ruleForm.xingbie" 
                placeholder="性别" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="教师姓名" prop="jiaoshixingming">
          <el-input v-model="ruleForm.jiaoshixingming" 
              placeholder="教师姓名" clearable  :readonly="ro.jiaoshixingming"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="教师姓名" prop="jiaoshixingming">
              <el-input v-model="ruleForm.jiaoshixingming" 
                placeholder="教师姓名" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="身高" prop="shengao">
          <el-input v-model="ruleForm.shengao" 
              placeholder="身高" clearable  :readonly="ro.shengao"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="身高" prop="shengao">
              <el-input v-model="ruleForm.shengao" 
                placeholder="身高" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="体重" prop="tizhong">
          <el-input v-model="ruleForm.tizhong" 
              placeholder="体重" clearable  :readonly="ro.tizhong"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="体重" prop="tizhong">
              <el-input v-model="ruleForm.tizhong" 
                placeholder="体重" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="血糖" prop="xuetang">
          <el-input v-model="ruleForm.xuetang" 
              placeholder="血糖" clearable  :readonly="ro.xuetang"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="血糖" prop="xuetang">
              <el-input v-model="ruleForm.xuetang" 
                placeholder="血糖" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="心率" prop="xinlv">
          <el-input v-model="ruleForm.xinlv" 
              placeholder="心率" clearable  :readonly="ro.xinlv"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="心率" prop="xinlv">
              <el-input v-model="ruleForm.xinlv" 
                placeholder="心率" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="胸围" prop="xiongwei">
          <el-input v-model="ruleForm.xiongwei" 
              placeholder="胸围" clearable  :readonly="ro.xiongwei"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="胸围" prop="xiongwei">
              <el-input v-model="ruleForm.xiongwei" 
                placeholder="胸围" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="血脂" prop="xuezhi">
          <el-input v-model="ruleForm.xuezhi" 
              placeholder="血脂" clearable  :readonly="ro.xuezhi"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="血脂" prop="xuezhi">
              <el-input v-model="ruleForm.xuezhi" 
                placeholder="血脂" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="肺活量" prop="feihuoliang">
          <el-input v-model="ruleForm.feihuoliang" 
              placeholder="肺活量" clearable  :readonly="ro.feihuoliang"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="肺活量" prop="feihuoliang">
              <el-input v-model="ruleForm.feihuoliang" 
                placeholder="肺活量" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="握力" prop="woli">
          <el-input v-model="ruleForm.woli" 
              placeholder="握力" clearable  :readonly="ro.woli"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="握力" prop="woli">
              <el-input v-model="ruleForm.woli" 
                placeholder="握力" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="input" v-if="type!='info'"  label="备注" prop="beizhu">
          <el-input v-model="ruleForm.beizhu" 
              placeholder="备注" clearable  :readonly="ro.beizhu"></el-input>
        </el-form-item>
        <div v-else>
          <el-form-item class="input" label="备注" prop="beizhu">
              <el-input v-model="ruleForm.beizhu" 
                placeholder="备注" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      <el-col :span="12">
        <el-form-item class="date" v-if="type!='info'" label="登记时间" prop="dengjishijian">
            <el-date-picker
                format="yyyy 年 MM 月 dd 日"
                value-format="yyyy-MM-dd"
                v-model="ruleForm.dengjishijian" 
                type="date"
                placeholder="登记时间">
            </el-date-picker> 
        </el-form-item>
        <div v-else>
          <el-form-item class="input" v-if="ruleForm.dengjishijian" label="登记时间" prop="dengjishijian">
              <el-input v-model="ruleForm.dengjishijian" 
                placeholder="登记时间" readonly></el-input>
          </el-form-item>
        </div>
      </el-col>
      </el-row>
      <el-form-item class="btn">
        <el-button v-if="type!='info'" type="primary" class="btn-success" @click="onSubmit">提交</el-button>
        <el-button v-if="type!='info'" class="btn-close" @click="back()">取消</el-button>
        <el-button v-if="type=='info'" class="btn-close" @click="back()">返回</el-button>
      </el-form-item>
    </el-form>
    

  </div>
</template>
<script>
// 数字，邮件，手机，url，身份证校验
import { isNumber,isIntNumer,isEmail,isPhone, isMobile,isURL,checkIdCard } from "@/utils/validate";
export default {
  data() {
    let self = this
    var validateIdCard = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!checkIdCard(value)) {
        callback(new Error("请输入正确的身份证号码"));
      } else {
        callback();
      }
    };
    var validateUrl = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isURL(value)) {
        callback(new Error("请输入正确的URL地址"));
      } else {
        callback();
      }
    };
    var validateMobile = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isMobile(value)) {
        callback(new Error("请输入正确的手机号码"));
      } else {
        callback();
      }
    };
    var validatePhone = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isPhone(value)) {
        callback(new Error("请输入正确的电话号码"));
      } else {
        callback();
      }
    };
    var validateEmail = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isEmail(value)) {
        callback(new Error("请输入正确的邮箱地址"));
      } else {
        callback();
      }
    };
    var validateNumber = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isNumber(value)) {
        callback(new Error("请输入数字"));
      } else {
        callback();
      }
    };
    var validateIntNumber = (rule, value, callback) => {
      if(!value){
        callback();
      } else if (!isIntNumer(value)) {
        callback(new Error("请输入整数"));
      } else {
        callback();
      }
    };
    return {
	  addEditForm: {"btnSaveFontColor":"#fff","selectFontSize":"14px","btnCancelBorderColor":"rgba(128, 128, 128, 1)","inputBorderRadius":"4px","inputFontSize":"14px","textareaBgColor":"#fff","btnSaveFontSize":"14px","textareaBorderRadius":"4px","uploadBgColor":"#fff","textareaBorderStyle":"solid","btnCancelWidth":"88px","textareaHeight":"120px","dateBgColor":"#fff","btnSaveBorderRadius":"4px","uploadLableFontSize":"14px","textareaBorderWidth":"1px","inputLableColor":"#606266","addEditBoxColor":"rgba(255, 255, 255, 0)","dateIconFontSize":"14px","btnSaveBgColor":"rgba(45, 98, 137, 1)","uploadIconFontColor":"#8c939d","textareaBorderColor":"#DCDFE6","btnCancelBgColor":"rgba(157, 157, 157, 1)","selectLableColor":"#606266","btnSaveBorderStyle":"solid","dateBorderWidth":"1px","dateLableFontSize":"14px","dateBorderRadius":"4px","btnCancelBorderStyle":"solid","selectLableFontSize":"14px","selectBorderStyle":"solid","selectIconFontColor":"#C0C4CC","btnCancelHeight":"44px","inputHeight":"40px","btnCancelFontColor":"rgba(255, 255, 255, 1)","dateBorderColor":"#DCDFE6","dateIconFontColor":"#C0C4CC","uploadBorderStyle":"solid","dateBorderStyle":"solid","dateLableColor":"#606266","dateFontSize":"14px","inputBorderWidth":"1px","uploadIconFontSize":"28px","selectHeight":"40px","inputFontColor":"#606266","uploadHeight":"148px","textareaLableColor":"#606266","textareaLableFontSize":"14px","btnCancelFontSize":"14px","inputBorderStyle":"solid","btnCancelBorderRadius":"4px","inputBgColor":"#fff","inputLableFontSize":"14px","uploadLableColor":"#606266","uploadBorderRadius":"4px","btnSaveHeight":"44px","selectBgColor":"#fff","btnSaveWidth":"88px","selectIconFontSize":"14px","dateHeight":"40px","selectBorderColor":"#DCDFE6","inputBorderColor":"#DCDFE6","uploadBorderColor":"#DCDFE6","textareaFontColor":"#606266","selectBorderWidth":"1px","dateFontColor":"#606266","btnCancelBorderWidth":"5px 0","uploadBorderWidth":"1px","textareaFontSize":"14px","selectBorderRadius":"4px","selectFontColor":"#606266","btnSaveBorderColor":"rgba(31, 63, 80, 1)","btnSaveBorderWidth":"5px 0"},
      id: '',
      type: '',
      ro:{
	xuehao : false,
	xingming : false,
	zhaopian : false,
	xingbie : false,
	jiaoshixingming : false,
	shengao : false,
	tizhong : false,
	xuetang : false,
	xinlv : false,
	xiongwei : false,
	xuezhi : false,
	feihuoliang : false,
	woli : false,
	beizhu : false,
	dengjishijian : false,
	userid : false,
      },
      ruleForm: {
        xuehao: '',
        xingming: '',
        zhaopian: '',
        xingbie: '',
        jiaoshixingming: '',
        shengao: '',
        tizhong: '',
        xuetang: '',
        xinlv: '',
        xiongwei: '',
        xuezhi: '',
        feihuoliang: '',
        woli: '',
        beizhu: '',
        dengjishijian: '',
        userid: '',
      },
      rules: {
          xuehao: [
          ],
          xingming: [
          ],
          zhaopian: [
          ],
          xingbie: [
          ],
          jiaoshixingming: [
          ],
          shengao: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          tizhong: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          xuetang: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          xinlv: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          xiongwei: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          xuezhi: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          feihuoliang: [
                { validator: validateNumber, trigger: 'blur' },
          ],
          woli: [
          ],
          beizhu: [
          ],
          dengjishijian: [
          ],
          userid: [
          ],
      }
    };
  },
  props: ["parent"],
  computed: {
  },
  created() {
	this.ruleForm.dengjishijian = this.getCurDate()
	this.addEditStyleChange()
	this.addEditUploadStyleChange()
  },
  methods: {
    // 下载
    download(file){
      window.open(`${file}`)
    },
    // 初始化
    init(id,type) {
      if (id) {
        this.id = id;
        this.type = type;
      }
      if(this.type=='info'||this.type=='else'){
        this.info(id);
      }else if(this.type=='logistics'){
        this.logistics=false;
        this.info(id);
      }else if(this.type=='cross'){
        var obj = this.$storage.getObj('crossObj');
        for (var o in obj){
          if(o=='xuehao'){
            this.ruleForm.xuehao = obj[o];
	    this.ro.xuehao = true;
            continue;
          }
          if(o=='xingming'){
            this.ruleForm.xingming = obj[o];
	    this.ro.xingming = true;
            continue;
          }
          if(o=='zhaopian'){
            this.ruleForm.zhaopian = obj[o];
	    this.ro.zhaopian = true;
            continue;
          }
          if(o=='xingbie'){
            this.ruleForm.xingbie = obj[o];
	    this.ro.xingbie = true;
            continue;
          }
          if(o=='jiaoshixingming'){
            this.ruleForm.jiaoshixingming = obj[o];
	    this.ro.jiaoshixingming = true;
            continue;
          }
          if(o=='shengao'){
            this.ruleForm.shengao = obj[o];
	    this.ro.shengao = true;
            continue;
          }
          if(o=='tizhong'){
            this.ruleForm.tizhong = obj[o];
	    this.ro.tizhong = true;
            continue;
          }
          if(o=='xuetang'){
            this.ruleForm.xuetang = obj[o];
	    this.ro.xuetang = true;
            continue;
          }
          if(o=='xinlv'){
            this.ruleForm.xinlv = obj[o];
	    this.ro.xinlv = true;
            continue;
          }
          if(o=='xiongwei'){
            this.ruleForm.xiongwei = obj[o];
	    this.ro.xiongwei = true;
            continue;
          }
          if(o=='xuezhi'){
            this.ruleForm.xuezhi = obj[o];
	    this.ro.xuezhi = true;
            continue;
          }
          if(o=='feihuoliang'){
            this.ruleForm.feihuoliang = obj[o];
	    this.ro.feihuoliang = true;
            continue;
          }
          if(o=='woli'){
            this.ruleForm.woli = obj[o];
	    this.ro.woli = true;
            continue;
          }
          if(o=='beizhu'){
            this.ruleForm.beizhu = obj[o];
	    this.ro.beizhu = true;
            continue;
          }
          if(o=='dengjishijian'){
            this.ruleForm.dengjishijian = obj[o];
	    this.ro.dengjishijian = true;
            continue;
          }
          if(o=='userid'){
            this.ruleForm.userid = obj[o];
	    this.ro.userid = true;
            continue;
          }
        }
      }
      // 获取用户信息
      this.$http({
        url: `${this.$storage.get('sessionTable')}/session`,
        method: "get"
      }).then(({ data }) => {
        if (data && data.code === 0) {
          var json = data.data;
		if(json.xuehao!=''&&json.xuehao){
                this.ruleForm.xuehao = json.xuehao
	    		this.ro.xuehao = true;
		}
		if(json.xingming!=''&&json.xingming){
                this.ruleForm.xingming = json.xingming
	    		this.ro.xingming = true;
		}
		if(json.zhaopian!=''&&json.zhaopian){
                this.ruleForm.zhaopian = json.zhaopian
	    		this.ro.zhaopian = true;
		}
		if(json.xingbie!=''&&json.xingbie){
                this.ruleForm.xingbie = json.xingbie
	    		this.ro.xingbie = true;
		}
		if(json.jiaoshixingming!=''&&json.jiaoshixingming){
                this.ruleForm.jiaoshixingming = json.jiaoshixingming
	    		this.ro.jiaoshixingming = true;
		}
        } else {
          this.$message.error(data.msg);
        }
      });
    },
    // 多级联动参数
    info(id) {
      this.$http({
        url: `shentisuzhiceping/info/${id}`,
        method: "get"
      }).then(({ data }) => {
        if (data && data.code === 0) {
        this.ruleForm = data.data;
	//解决前台上传图片后台不显示的问题
	let reg=new RegExp('../../../upload','g')//g代表全部
        } else {
          this.$message.error(data.msg);
        }
      });
    },
    // 提交
    onSubmit() {






	if(this.ruleForm.zhaopian!=null) {
		this.ruleForm.zhaopian = this.ruleForm.zhaopian.replace(new RegExp(this.$base.url,"g"),"");
	}



























var objcross = this.$storage.getObj('crossObj');

      //更新跨表属性
       var crossuserid;
       var crossrefid;
       var crossoptnum;
       if(this.type=='cross'){
                var statusColumnName = this.$storage.get('statusColumnName');
                var statusColumnValue = this.$storage.get('statusColumnValue');
                if(statusColumnName!='') {
                        var obj = this.$storage.getObj('crossObj');
                       if(!statusColumnName.startsWith("[")) {
                               for (var o in obj){
                                 if(o==statusColumnName){
                                   obj[o] = statusColumnValue;
                                 }
                               }
                               var table = this.$storage.get('crossTable');
                             this.$http({
                                 url: `${table}/update`,
                                 method: "post",
                                 data: obj
                               }).then(({ data }) => {});
                       } else {
                               crossuserid=this.$storage.get('userid');
                               crossrefid=obj['id'];
                               crossoptnum=this.$storage.get('statusColumnName');
                               crossoptnum=crossoptnum.replace(/\[/,"").replace(/\]/,"");
                        }
                }
        }
       this.$refs["ruleForm"].validate(valid => {
         if (valid) {
		 if(crossrefid && crossuserid) {
			 this.ruleForm.crossuserid = crossuserid;
			 this.ruleForm.crossrefid = crossrefid;
			let params = { 
				page: 1, 
				limit: 10, 
				crossuserid:this.ruleForm.crossuserid,
				crossrefid:this.ruleForm.crossrefid,
			} 
			this.$http({ 
				url: "shentisuzhiceping/page", 
				method: "get", 
				params: params 
			}).then(({ 
				data 
			}) => { 
				if (data && data.code === 0) { 
				       if(data.data.total>=crossoptnum) {
					     this.$message.error(this.$storage.get('tips'));
					       return false;
				       } else {
					 this.$http({
					   url: `shentisuzhiceping/${!this.ruleForm.id ? "save" : "update"}`,
					   method: "post",
					   data: this.ruleForm
					 }).then(({ data }) => {
					   if (data && data.code === 0) {
					     this.$message({
					       message: "操作成功",
					       type: "success",
					       duration: 1500,
					       onClose: () => {
						 this.parent.showFlag = true;
						 this.parent.addOrUpdateFlag = false;
						 this.parent.shentisuzhicepingCrossAddOrUpdateFlag = false;
						 this.parent.search();
						 this.parent.contentStyleChange();
					       }
					     });
					   } else {
					     this.$message.error(data.msg);
					   }
					 });

				       }
				} else { 
				} 
			});
		 } else {
			 this.$http({
			   url: `shentisuzhiceping/${!this.ruleForm.id ? "save" : "update"}`,
			   method: "post",
			   data: this.ruleForm
			 }).then(({ data }) => {
			   if (data && data.code === 0) {
			     this.$message({
			       message: "操作成功",
			       type: "success",
			       duration: 1500,
			       onClose: () => {
				 this.parent.showFlag = true;
				 this.parent.addOrUpdateFlag = false;
				 this.parent.shentisuzhicepingCrossAddOrUpdateFlag = false;
				 this.parent.search();
				 this.parent.contentStyleChange();
			       }
			     });
			   } else {
			     this.$message.error(data.msg);
			   }
			 });
		 }
         }
       });
    },
    // 获取uuid
    getUUID () {
      return new Date().getTime();
    },
    // 返回
    back() {
      this.parent.showFlag = true;
      this.parent.addOrUpdateFlag = false;
      this.parent.shentisuzhicepingCrossAddOrUpdateFlag = false;
      this.parent.contentStyleChange();
    },
    zhaopianUploadChange(fileUrls) {
	this.ruleForm.zhaopian = fileUrls;
	this.addEditUploadStyleChange()
    },
	addEditStyleChange() {
	  this.$nextTick(()=>{
	    // input
	    document.querySelectorAll('.addEdit-block .input .el-input__inner').forEach(el=>{
	      el.style.height = this.addEditForm.inputHeight
	      el.style.color = this.addEditForm.inputFontColor
	      el.style.fontSize = this.addEditForm.inputFontSize
	      el.style.borderWidth = this.addEditForm.inputBorderWidth
	      el.style.borderStyle = this.addEditForm.inputBorderStyle
	      el.style.borderColor = this.addEditForm.inputBorderColor
	      el.style.borderRadius = this.addEditForm.inputBorderRadius
	      el.style.backgroundColor = this.addEditForm.inputBgColor
	    })
	    document.querySelectorAll('.addEdit-block .input .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.inputHeight
	      el.style.color = this.addEditForm.inputLableColor
	      el.style.fontSize = this.addEditForm.inputLableFontSize
	    })
	    // select
	    document.querySelectorAll('.addEdit-block .select .el-input__inner').forEach(el=>{
	      el.style.height = this.addEditForm.selectHeight
	      el.style.color = this.addEditForm.selectFontColor
	      el.style.fontSize = this.addEditForm.selectFontSize
	      el.style.borderWidth = this.addEditForm.selectBorderWidth
	      el.style.borderStyle = this.addEditForm.selectBorderStyle
	      el.style.borderColor = this.addEditForm.selectBorderColor
	      el.style.borderRadius = this.addEditForm.selectBorderRadius
	      el.style.backgroundColor = this.addEditForm.selectBgColor
	    })
	    document.querySelectorAll('.addEdit-block .select .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.selectHeight
	      el.style.color = this.addEditForm.selectLableColor
	      el.style.fontSize = this.addEditForm.selectLableFontSize
	    })
	    document.querySelectorAll('.addEdit-block .select .el-select__caret').forEach(el=>{
	      el.style.color = this.addEditForm.selectIconFontColor
	      el.style.fontSize = this.addEditForm.selectIconFontSize
	    })
	    // date
	    document.querySelectorAll('.addEdit-block .date .el-input__inner').forEach(el=>{
	      el.style.height = this.addEditForm.dateHeight
	      el.style.color = this.addEditForm.dateFontColor
	      el.style.fontSize = this.addEditForm.dateFontSize
	      el.style.borderWidth = this.addEditForm.dateBorderWidth
	      el.style.borderStyle = this.addEditForm.dateBorderStyle
	      el.style.borderColor = this.addEditForm.dateBorderColor
	      el.style.borderRadius = this.addEditForm.dateBorderRadius
	      el.style.backgroundColor = this.addEditForm.dateBgColor
	    })
	    document.querySelectorAll('.addEdit-block .date .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.dateHeight
	      el.style.color = this.addEditForm.dateLableColor
	      el.style.fontSize = this.addEditForm.dateLableFontSize
	    })
	    document.querySelectorAll('.addEdit-block .date .el-input__icon').forEach(el=>{
	      el.style.color = this.addEditForm.dateIconFontColor
	      el.style.fontSize = this.addEditForm.dateIconFontSize
	      el.style.lineHeight = this.addEditForm.dateHeight
	    })
	    // upload
	    let iconLineHeight = parseInt(this.addEditForm.uploadHeight) - parseInt(this.addEditForm.uploadBorderWidth) * 2 + 'px'
	    document.querySelectorAll('.addEdit-block .upload .el-upload--picture-card').forEach(el=>{
	      el.style.width = this.addEditForm.uploadHeight
	      el.style.height = this.addEditForm.uploadHeight
	      el.style.borderWidth = this.addEditForm.uploadBorderWidth
	      el.style.borderStyle = this.addEditForm.uploadBorderStyle
	      el.style.borderColor = this.addEditForm.uploadBorderColor
	      el.style.borderRadius = this.addEditForm.uploadBorderRadius
	      el.style.backgroundColor = this.addEditForm.uploadBgColor
	    })
	    document.querySelectorAll('.addEdit-block .upload .el-form-item__label').forEach(el=>{
	      el.style.lineHeight = this.addEditForm.uploadHeight
	      el.style.color = this.addEditForm.uploadLableColor
	      el.style.fontSize = this.addEditForm.uploadLableFontSize
	    })
	    document.querySelectorAll('.addEdit-block .upload .el-icon-plus').forEach(el=>{
	      el.style.color = this.addEditForm.uploadIconFontColor
	      el.style.fontSize = this.addEditForm.uploadIconFontSize
	      el.style.lineHeight = iconLineHeight
	      el.style.display = 'block'
	    })
	    // 多文本输入框
	    document.querySelectorAll('.addEdit-block .textarea .el-textarea__inner').forEach(el=>{
	      el.style.height = this.addEditForm.textareaHeight
	      el.style.color = this.addEditForm.textareaFontColor
	      el.style.fontSize = this.addEditForm.textareaFontSize
	      el.style.borderWidth = this.addEditForm.textareaBorderWidth
	      el.style.borderStyle = this.addEditForm.textareaBorderStyle
	      el.style.borderColor = this.addEditForm.textareaBorderColor
	      el.style.borderRadius = this.addEditForm.textareaBorderRadius
	      el.style.backgroundColor = this.addEditForm.textareaBgColor
	    })
	    document.querySelectorAll('.addEdit-block .textarea .el-form-item__label').forEach(el=>{
	      // el.style.lineHeight = this.addEditForm.textareaHeight
	      el.style.color = this.addEditForm.textareaLableColor
	      el.style.fontSize = this.addEditForm.textareaLableFontSize
	    })
	    // 保存
	    document.querySelectorAll('.addEdit-block .btn .btn-success').forEach(el=>{
	      el.style.width = this.addEditForm.btnSaveWidth
	      el.style.height = this.addEditForm.btnSaveHeight
	      el.style.color = this.addEditForm.btnSaveFontColor
	      el.style.fontSize = this.addEditForm.btnSaveFontSize
	      el.style.borderWidth = this.addEditForm.btnSaveBorderWidth
	      el.style.borderStyle = this.addEditForm.btnSaveBorderStyle
	      el.style.borderColor = this.addEditForm.btnSaveBorderColor
	      el.style.borderRadius = this.addEditForm.btnSaveBorderRadius
	      el.style.backgroundColor = this.addEditForm.btnSaveBgColor
	    })
	    // 返回
	    document.querySelectorAll('.addEdit-block .btn .btn-close').forEach(el=>{
	      el.style.width = this.addEditForm.btnCancelWidth
	      el.style.height = this.addEditForm.btnCancelHeight
	      el.style.color = this.addEditForm.btnCancelFontColor
	      el.style.fontSize = this.addEditForm.btnCancelFontSize
	      el.style.borderWidth = this.addEditForm.btnCancelBorderWidth
	      el.style.borderStyle = this.addEditForm.btnCancelBorderStyle
	      el.style.borderColor = this.addEditForm.btnCancelBorderColor
	      el.style.borderRadius = this.addEditForm.btnCancelBorderRadius
	      el.style.backgroundColor = this.addEditForm.btnCancelBgColor
	    })
	  })
	},
	addEditUploadStyleChange() {
		this.$nextTick(()=>{
		  document.querySelectorAll('.addEdit-block .upload .el-upload-list--picture-card .el-upload-list__item').forEach(el=>{
			el.style.width = this.addEditForm.uploadHeight
			el.style.height = this.addEditForm.uploadHeight
			el.style.borderWidth = this.addEditForm.uploadBorderWidth
			el.style.borderStyle = this.addEditForm.uploadBorderStyle
			el.style.borderColor = this.addEditForm.uploadBorderColor
			el.style.borderRadius = this.addEditForm.uploadBorderRadius
			el.style.backgroundColor = this.addEditForm.uploadBgColor
		  })
	  })
	},
  }
};
</script>
<style lang="scss">
.editor{
  height: 500px;
  
  & /deep/ .ql-container {
	  height: 310px;
  }
}
.amap-wrapper {
  width: 100%;
  height: 500px;
}
.search-box {
  position: absolute;
}
.addEdit-block {
	margin: -10px;
}
.detail-form-content {
	padding: 12px;
	background-color: transparent;
}
.btn .el-button {
  padding: 0;
}
</style>
