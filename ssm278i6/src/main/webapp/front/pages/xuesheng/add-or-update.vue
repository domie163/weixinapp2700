<template>
	<view class="content">
		<form class="app-update-pv">
			
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">学号</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.xuehao" v-model="ruleForm.xuehao" placeholder="学号"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">姓名</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.xingming" v-model="ruleForm.xingming" placeholder="姓名"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">密码</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.mima" v-model="ruleForm.mima" placeholder="密码"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group select">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"160rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">性别</view>
				<picker @change="xingbieChange" :value="xingbieIndex"  :range="xingbieOptions">
					<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' class="uni-input">{{ruleForm.xingbie?ruleForm.xingbie:"请选择性别"}}</view>
				</picker>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">身份证</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.shenfenzheng" v-model="ruleForm.shenfenzheng" placeholder="身份证"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">手机</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.shouji" v-model="ruleForm.shouji" placeholder="手机"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">邮箱</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.youxiang" v-model="ruleForm.youxiang" placeholder="邮箱"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">学院</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.xueyuan" v-model="ruleForm.xueyuan" placeholder="学院"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">专业</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.zhuanye" v-model="ruleForm.zhuanye" placeholder="专业"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"170rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">班级</view>
				<input :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0.19)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' :disabled="ro.banji" v-model="ruleForm.banji" placeholder="班级"></input>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 20rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group" @tap="zhaopianTap" :class='left == "left"?"":"active"'>
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"160rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">照片</view>
				<view class="right-input" :style='{textAlign:"left"}' style="padding:0">
					<image :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","borderRadius":"100%","textAlign":"left","borderWidth":"0","width":"88rpx","borderStyle":"solid","height":"88rpx"}' class="avator" v-if="ruleForm.zhaopian" :src="baseUrl+ruleForm.zhaopian" mode="aspectFill"></image>
					<image :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","borderRadius":"100%","textAlign":"left","borderWidth":"0","width":"88rpx","borderStyle":"solid","height":"88rpx"}' class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
				</view>
			</view>
			<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","padding":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(51, 153, 153, 1)","margin":"0 0 10rpx 0","borderRadius":"0","borderWidth":"2rpx","width":"100%","borderStyle":"solid","height":"108rpx"}' class="cu-form-group select">
				<view :style='{"padding":"0","boxShadow":"0 0 16rpx rgba(0,0,0,0)","margin":"0","borderColor":"#ccc","backgroundColor":"rgba(0,0,0,0)","color":"rgba(51, 153, 153, 1)","textAlign":"left","borderRadius":"0","borderWidth":"0","width":"160rpx","fontSize":"28rpx","lineHeight":"80rpx","borderStyle":"solid"}' class="title">教师姓名</view>
				<picker @change="jiaoshixingmingChange" :value="jiaoshixingmingIndex"  :range="jiaoshixingmingOptions">
					<view :style='{"boxShadow":"0 0 0px rgba(0,0,0,.6) inset","padding":"0 30rpx","backgroundColor":"rgba(255, 255, 255, 0)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"16rpx","borderWidth":"2rpx","width":"calc(100% - 160rpx)","fontSize":"28rpx","borderStyle":"solid","height":"88rpx"}' class="uni-input">{{ruleForm.jiaoshixingming?ruleForm.jiaoshixingming:"请选择教师姓名"}}</view>
				</picker>
			</view>
			
			<!-- 否 -->
 

			
			
			<view class="btn">
				<button :style='{"boxShadow":"0 0 0px rgba(0,0,0,0) inset","padding":"0","backgroundColor":"rgba(51, 153, 153, 1)","borderColor":"rgba(51, 153, 153, 1)","margin":"0","borderRadius":"8rpx","color":"#fff","borderWidth":"1","width":"80%","fontSize":"28rpx","borderStyle":"solid","height":"80rpx"}' @tap="onSubmitTap" class="bg-red">提交</button>
			</view>
		</form>

			
	</view>
</template>

<script>
	import wPicker from "@/components/w-picker/w-picker.vue";

	export default {
		data() {
			return {
				cross:'',
				ruleForm: {
				xuehao: '',
				xingming: '',
				mima: '',
				xingbie: '',
				shenfenzheng: '',
				shouji: '',
				youxiang: '',
				xueyuan: '',
				zhuanye: '',
				banji: '',
				zhaopian: '',
				jiaoshixingming: '',
				},
				xingbieOptions: [],
				xingbieIndex: 0,
				jiaoshixingmingOptions: [],
				jiaoshixingmingIndex: 0,
				// 登陆用户信息
				user: {},
                                ro:{
                                   xuehao : false,
                                   xingming : false,
                                   mima : false,
                                   xingbie : false,
                                   shenfenzheng : false,
                                   shouji : false,
                                   youxiang : false,
                                   xueyuan : false,
                                   zhuanye : false,
                                   banji : false,
                                   zhaopian : false,
                                   jiaoshixingming : false,
                                },
			}
		},
		components: {
			wPicker
		},
		computed: {
			baseUrl() {
				return this.$base.url;
			},
			
			
			
			
			
			
			
			
			
			
			
			
		},
		async onLoad(options) {
			let table = uni.getStorageSync("nowTable");
			// 获取用户信息
			let res = await this.$api.session(table);
			this.user = res.data;
			
			// ss读取


			// 自定义下拉框值
			this.xingbieOptions = "男,女".split(',')
			// 下拉框
			res = await this.$api.option(`jiaoshi`,`jiaoshixingming`,{});
			this.jiaoshixingmingOptions = res.data;

			// 如果有登陆，获取登陆后保存的userid
			this.ruleForm.userid = uni.getStorageSync("userid")
			if (options.refid) {
				// 如果上一级页面传递了refid，获取改refid数据信息
				this.ruleForm.refid = options.refid;
				this.ruleForm.nickname = uni.getStorageSync("nickname");
			}
			// 如果是更新操作
			if (options.id) {
				this.ruleForm.id = options.id;
				// 获取信息
				res = await this.$api.info(`xuesheng`, this.ruleForm.id);
				this.ruleForm = res.data;
			}
			// 跨表
			this.cross = options.cross;
			if(options.cross){
				var obj = uni.getStorageSync('crossObj');
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
					if(o=='mima'){
					this.ruleForm.mima = obj[o];
					this.ro.mima = true;
					continue;
					}
					if(o=='xingbie'){
					this.ruleForm.xingbie = obj[o];
					this.ro.xingbie = true;
					continue;
					}
					if(o=='shenfenzheng'){
					this.ruleForm.shenfenzheng = obj[o];
					this.ro.shenfenzheng = true;
					continue;
					}
					if(o=='shouji'){
					this.ruleForm.shouji = obj[o];
					this.ro.shouji = true;
					continue;
					}
					if(o=='youxiang'){
					this.ruleForm.youxiang = obj[o];
					this.ro.youxiang = true;
					continue;
					}
					if(o=='xueyuan'){
					this.ruleForm.xueyuan = obj[o];
					this.ro.xueyuan = true;
					continue;
					}
					if(o=='zhuanye'){
					this.ruleForm.zhuanye = obj[o];
					this.ro.zhuanye = true;
					continue;
					}
					if(o=='banji'){
					this.ruleForm.banji = obj[o];
					this.ro.banji = true;
					continue;
					}
					if(o=='zhaopian'){
					this.ruleForm.zhaopian = obj[o];
					this.ro.zhaopian = true;
					continue;
					}
					if(o=='jiaoshixingming'){
					this.ruleForm.jiaoshixingming = obj[o];
					this.ro.jiaoshixingming = true;
					continue;
					}
				}
			}
			this.styleChange()
		},
		methods: {
			styleChange() {
				this.$nextTick(()=>{
					// document.querySelectorAll('.app-update-pv .cu-form-group .uni-input-input').forEach(el=>{
					//   el.style.backgroundColor = this.addUpdateForm.input.content.backgroundColor
					// })
				})
			},

			// 多级联动参数



			// 下拉变化
			xingbieChange(e) {
				this.xingbieIndex = e.target.value
				this.ruleForm.xingbie = this.xingbieOptions[this.xingbieIndex]
			},
			// 下拉变化
			jiaoshixingmingChange(e) {
				this.jiaoshixingmingIndex = e.target.value
				this.ruleForm.jiaoshixingming = this.jiaoshixingmingOptions[this.jiaoshixingmingIndex]
			},

			zhaopianTap() {
				let _this = this;
				this.$api.upload(function(res) {
					_this.ruleForm.zhaopian = 'upload/' + res.file;
					_this.$forceUpdate();
					_this.$nextTick(()=>{
						_this.styleChange()
					})
				});
			},

			getUUID () {
				return new Date().getTime();
			},
			async onSubmitTap() {
























//跨表计算判断
				if((!this.ruleForm.xuehao)){
					this.$utils.msg(`学号不能为空`);
					return
				}
				if((!this.ruleForm.xingming)){
					this.$utils.msg(`姓名不能为空`);
					return
				}
				if((!this.ruleForm.mima)){
					this.$utils.msg(`密码不能为空`);
					return
				}
				if(this.ruleForm.shenfenzheng&&(!this.$validate.checkIdCard(this.ruleForm.shenfenzheng))){
					this.$utils.msg(`身份证应输入身份证格式`);
					return
				}
				if(this.ruleForm.shouji&&(!this.$validate.isMobile(this.ruleForm.shouji))){
					this.$utils.msg(`手机应输入手机格式`);
					return
				}
				if(this.ruleForm.youxiang&&(!this.$validate.isEmail(this.ruleForm.youxiang))){
					this.$utils.msg(`邮箱应输入邮件格式`);
					return
				}
				//更新跨表属性
			       var crossuserid;
			       var crossrefid;
			       var crossoptnum;
				if(this.cross){
					var statusColumnName = uni.getStorageSync('statusColumnName');
					var statusColumnValue = uni.getStorageSync('statusColumnValue');
					if(statusColumnName!='') {
						var obj = uni.getStorageSync('crossObj');
						if(!statusColumnName.startsWith("[")) {
							for (var o in obj){
								if(o==statusColumnName){
									obj[o] = statusColumnValue;
								}

							}
							var table = uni.getStorageSync('crossTable');
							await this.$api.update(`${table}`, obj);
						} else {
						       crossuserid=Number(uni.getStorageSync('userid'));
						       crossrefid=obj['id'];
						       crossoptnum=uni.getStorageSync('statusColumnName');
						       crossoptnum=crossoptnum.replace(/\[/,"").replace(/\]/,"");
						}
					}
				}
				if(crossrefid && crossuserid) {
					this.ruleForm.crossuserid=crossuserid;
					this.ruleForm.crossrefid=crossrefid;
					let params = {
						page: 1,
						limit:10,
						crossuserid:crossuserid,
						crossrefid:crossrefid,
					}
					let res = await this.$api.list(`xuesheng`, params);
					if (res.data.total >= crossoptnum) {
						this.$utils.msg(uni.getStorageSync('tips'));
						return false;
					} else {
                //跨表计算
						if(this.ruleForm.id){
							await this.$api.update(`xuesheng`, this.ruleForm);
						}else{
							await this.$api.add(`xuesheng`, this.ruleForm);
						}
						this.$utils.msgBack('提交成功');
					}
				} else {
                //跨表计算
					if(this.ruleForm.id){
						await this.$api.update(`xuesheng`, this.ruleForm);
					}else{
						await this.$api.add(`xuesheng`, this.ruleForm);
					}
					this.$utils.msgBack('提交成功');
				}
			},
			optionsChange(e) {
				this.index = e.target.value
			},
			bindDateChange(e) {
				this.date = e.target.value
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			toggleTab(str) {
				this.$refs[str].show();
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container {
		padding: 20upx;
	}
	
	.content:after {
		position: fixed;
		top: 0;
		right: 0;
		left: 0;
		bottom: 0;
		content: '';
		background-attachment: fixed;
		background-size: cover;
		background-position: center;
	}

	textarea {
		border: 1upx solid #EEEEEE;
		border-radius: 20upx;
		padding: 20upx;
	}

	.title {
		width: 180upx;
	}

	.avator {
		width: 150upx;
		height: 60upx;
	}

	.right-input {
		flex: 1;
		text-align: left;
		padding: 0 24upx;
	}
	
	.cu-form-group.active {
		justify-content: space-between;
	}
	
	.btn {
	  display: flex;
	  align-items: center;
	  justify-content: center;
	  flex-wrap: wrap;
	  padding: 20upx 0;
	}
	
	.cu-form-group {
		padding: 0 24upx;
		background-color: transparent;
		min-height: inherit;
	}
	
	.cu-form-group+.cu-form-group {
		border: 0;
	}
	
	.cu-form-group uni-input {
		padding: 0 30upx;
	}
	
	.uni-input {
		padding: 0 30upx;
	}
	
	.cu-form-group uni-textarea {
		padding: 30upx;
		margin: 0;
	}
	
	.cu-form-group uni-picker::after {
		line-height: 88rpx;
	}
	
	.select .uni-input {
		line-height: 88rpx;
	}
	
	.input .right-input {
		line-height: 88rpx;
	}
</style>
