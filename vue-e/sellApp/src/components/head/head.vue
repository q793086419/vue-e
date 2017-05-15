<template>
  <div class="head">
  	<!-- 店名、送达时间、优惠信息 -->
    <div class="content-wrapper">
     	<div class="avatar">
     		<img width="64" height="64" v-bind:src="seller.data.avatar">
     	</div>
     	<div class="content">
     		<div class="title">
     			<span class="brand"></span>
     			<span class="name">{{seller.data.name}}</span>
     		</div>
     		<div class="description">
     			{{seller.data.description}}/{{seller.data.deliveryTime}}分钟送达
     		</div>
     		<div v-if="seller.data.supports" class="supports">
     			<span class="icon" v-bind:class="classMap[seller.data.supports[0].type]"></span>
     			<span class="text">{{seller.data.supports[0].description}}</span>
     		</div>
     	</div>
     	<div class="support-count">
     		<span class="count">{{seller.data.supports.length}}个</span>
     		<i class="icon-thumb_up"></i>
     	</div>
    </div>
    <!-- 公告 -->
    <div class="bulletin-wrapper">
    	<span class="bulletin-title"></span><span class="bulletin-text">{{ seller.data.bulletin }}</span><i class="icon-thumb_up"></i>
    </div>
    <!-- 背景图 -->
    <div class="background">
    	<img v-bind:src="seller.data.avatar">
    </div>
  </div>
</template>

<script type='text/ecmascript-6'>
export default{
  props: {
    seller: {
      type: Object
    }
  },
  created () {
    this.classMap = ['decrease', 'discount', 'invoice', 'special', 'guarantee'];
  }
};
</script>

<style lang="less" scoped>
@import '../../common/style/mixin.less';

.head{
	position: relative;
	color: #ffffff;
	background-color: rgba(7,17,27,0.5);
	.content-wrapper{
		position: relative;
		padding: 24px 12px 18px 24px;
		font-size: 0;
		.avatar{
			display: inline-block;
			vertical-align: top;
			img{
				border-radius: 2px;
			}
		}
		.content{
			display: inline-block;
			font-size: 14px;
			margin-left: 16px;
			.title{
				margin-top: 2px;
				margin-bottom: 8px;
				.brand{
					width: 30px;
					height: 18px;
					display: inline-block;
					.bg-image('brand');
					background-size: 30px 18px;
					background-repeat: no-repeat;
					vertical-align: top;
				}
				.name{
					margin-left: 6px;
					font-size: 16px;
					font-weight: 700;
					line-height: 18px;
					color: #ffffff;
				}
			}
			.description{
				margin-bottom: 10px;
				line-height: 12px;
				font-size: 12px;
			}
			.supports{
				.icon{
					vertical-align: top;
					display: inline-block;
					width: 12px;
					height: 12px;
					margin-right: 4px;
					background-size: 12px 12px;
					background-repeat: no-repeat;
					&.decrease{
						.bg-image('decrease_1');
					}
					&.discount{
						.bg-image('discount_1');
					}
					&.invoice{
						.bg-image('invoice_1');
					}
					&.special{
						.bg-image('special_1');
					}
					&.guarantee{
						.bg-image('guarantee_1');
					}
				}
				.text{
					vertical-align: top;
					line-height: 12px;
					font-size: 12px;
				}
			}
		}
		.support-count{
			position: absolute;
			right: 12px;
			bottom: 18px;
			height: 24px;
			padding:0 8px;
			line-height: 24px;
			border-radius: 14px;
			background:rgba(0,0,0,0.2);
			text-align: center;
			.count{
				font-size: 10px;
				vertical-align: top;
				line-height: 24px;
				font-size: 12px;
			}
			.icon-thumb_up{
				margin-left: 2px;
				vertical-align: top;
				line-height: 24px;
				font-size: 10px;
			}
		}
	}
	.bulletin-wrapper{
		position: relative;
		height: 28px;
		line-height: 28px;
		padding: 0 22px 0 12px;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
		background-color: rgba(7,17,27,0.2);
		.bulletin-title{
			display: inline-block;
			vertical-align:top;
			margin-top: 7px;
			width: 22px;
			height: 12px;
			.bg-image('bulletin');
			background-size: 22px 12px;
			background-repeat: no-repeat;
		}
		.bulletin-text{
			font-size: 10px;
			margin-left: 4px;
			margin-right: 4px;
			vertical-align: top;
		}
		.icon-thumb_up{
			position: absolute;
			font-size: 10px;
			right: 12px;
			bottom: 8px;
		}
	}
	.background{
		img{
			position: absolute;
			top: 0;
			left: 0;
			height: 100%;
			width: 100%;
			z-index: -1;
			filter:blur(10px);
		}
	}
}
</style>
