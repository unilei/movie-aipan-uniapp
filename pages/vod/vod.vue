<template>
	<view>
		<!-- https://www.nihaowua.com/v/video.php -->
		<view v-if="isShow" class="vod-video">
			<video id="video" :src="videoSrc" controls autoplay page-gesture play-btn-position="center"
				enable-play-gesture></video>
			<view class="video-button">
				<view class="video-download-button">
					<button type="default" @click="downloadVideo(videoSrc)">缓存</button>
				</view>
			</view>
		</view>
		<view v-if="!isShow">
			<view class="container">
				<view class="shi-container">
					<view class="shi-img">
						<image src="../../static/2973.jpg" mode="widthFix"></image>
					</view>
					<view class="shi-title">出塞</view>
					<view class="shi-author">[唐] 王昌龄</view>
					<view class="shi-content">
						秦时明月汉时关，万里长征人未还 <br>
						但使龙城飞将在，不教胡马度阴山
					</view>
				</view>
				<view class="my-container">
					<text>
						这是一首慨叹边战不断，国无良将的边塞诗。诗的首句最耐人寻味。说的是此地
						汉关，明月秦时，大有历史变换，征战未断的感叹。二句写征人未还，多少儿男战死
						沙场，留下多少悲剧。三、四句写出千百年来人民的共同意愿，冀望有“龙城飞将”
						出现，平息胡乱，安定边防。全诗以平凡的语言，唱出雄浑豁达的主旨，气势流畅，
						一气呵成，吟之莫不叫绝。明人李攀龙曾推奖它是唐代七绝压卷之作，实不过分。

						--引自"超纯斋诗词"bookbest.163.net 翻译、评析：刘建勋

						这是一首名作，明代诗人李攀龙曾经推奖它唐人七绝的压卷之作。清沈德潜《说诗ㄧ语》说：“‘秦时明月’一章，前人推奖之而未言其妙，盖言师劳力竭，而功不成，由将非其人之故；得飞将军备边，边烽自熄，即高常侍《燕歌行》归重‘至今人说李将军’也。防边筑城，起于秦汉，明月属秦，关属汉，诗中互文。”他这段话批评李攀龙只知推奖此诗而未言其妙，可是他自己也只是说明了全诗的主旨，并没有点出作者的匠心。

						沈氏归纳的全诗的主旨基本是对的，但这个主旨的思想是很平凡的。为什么这样平凡的思想竟能写成为一首压卷的绝作呢？原来，这首诗里，有一句最美最耐人寻味的诗句，即开头第一句：“秦时明月汉时关”。这句诗有什么妙处呢？得从诗题说起。此诗题名《出塞》，一望而知是一首乐府诗。乐府诗是要谱成乐章、广泛传唱的，为入谱传唱的需要，诗中就往往有一些常见习用的词语。王昌龄这首诗也不例外。你看这开头一句中的“明月”和“关”两个词，正是有关边塞的乐府诗里很常见的词语。?独指??
						横吹曲辞》里不是就有《关山月》吗？《乐府解题》说：“关山月，伤离别也。”无论征人思家，思妇怀远，往往都离不了这“关”和“月”两个字。“关山三五月，客子忆秦川”（徐陵《关山月》），“关山夜月明，秋色照孤城”（王褒《关山月》），“关山万里不可越，谁能坐对芳菲月”（卢思道《从军行》），“
						陇头明月迥临关，陇上行人夜吹笛”（王维《陇头吟》），例子举不胜举。看清这一点之后，你就明白这句诗的新鲜奇妙之处，就是在“明月”和“关”两个词之前增加了“秦”、“汉”两个时间性的限定词。

						这样从千年以前、万里之外下笔，自然形成了一种雄浑苍茫的独特的意境，借用前代评诗惯用的词语来说，就是“发兴高远”，使读者把眼前明月下的边关同秦代筑关备胡，汉代在关内外与胡人发生一系列战争的悠久历史自然联系起来。这样一来，“万里长征人未还”，就不只是当代的人们，而是自秦汉以来世世代代的人们共同的悲剧；希望边境有“不教胡马度阴山”的“龙城飞将”，也不只是汉代的人们，而是世世代代人们共同的愿望。平凡的悲剧，平凡的希望，都随着首句“秦”、“汉”这两个时间限定词的出现而显示出很不平凡的意义。这句诗声调高昂，气势雄浑，也足以统摄全篇。诗歌之美，诗歌语言之美，往往就表现在似乎很平凡的字上，或者说，就表现在把似乎很平凡的字用在最确切最关键的地方。而这些地方，往往又最能体现诗人高超的艺术造诣。

						（廖仲安）
					</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				videoSrc: '',
				isShow: false
			}
		},
		created() {
			var self = this;
			uni.getClipboardData({
				success(res) {
					console.log(res)

					let str = res.data;
					let obj = JSON.parse(str)
					if (obj.isLei == 1) {
						self.isShow = true;
						self.videoSrc = obj.url;
					}
				}
			})
		},
		onLoad() {
			// var self = this;
			// uni.getClipboardData({
			// 	success(res) {
			// 		console.log(res)

			// 		let str = res.data;
			// 		let obj = JSON.parse(str)
			// 		if(obj.isLei==1){
			// 			self.isShow = true;
			// 			self.videoSrc = obj.url;
			// 		}
			// 	}
			// })
		},
		methods: {
			downloadVideo(src){
				const downloadTask = uni.downloadFile({
				    url: src, //仅为示例，并非真实的资源
				    success: (res) => {
				        if (res.statusCode === 200) {
				            console.log('下载成功');
				        }
				    }
				});
				
				downloadTask.onProgressUpdate((res) => {
				    console.log('下载进度' + res.progress);
				    console.log('已经下载的数据长度' + res.totalBytesWritten);
				    console.log('预期需要下载的数据总长度' + res.totalBytesExpectedToWrite);
				
				    // 测试条件，取消下载任务。
				    if (res.progress > 50) {
				        downloadTask.abort();
				    }
				});
			}
		}
	}
</script>

<style>
	page{
		background-color: #000000;
	}
	.vod-video {
		width: 100%;
		height: 90%;
		text-align: center;
		position: fixed;
		z-index: 100;
		top: 0;
		bottom: 0;
		right: 0;
		left: 0;
		margin: auto;
	}
	#video{
		width: 100%;
		height: 100%;
		/* height: 800rpx; */
	}

	.shi-container {
		padding: 20rpx;
	}

	.shi-img {
		width: 98%;
		margin: 0 auto;
	}

	.shi-img image {
		width: 100%;
	}

	.shi-title {
		font-size: 34rpx;
		font-weight: 700;
		text-align: center;
		color: #FFFFFF;
	}

	.shi-author {
		font-size: 28rpx;
		text-align: center;
		color: #808080;
	}

	.shi-content {
		text-align: center;
		font-size: 30rpx;
		color: #FFFFFF;
	}

	.my-container {
		padding: 20rpx;
		color: #888888;
		border-top: 1rpx solid #EEEEEE;
	}
	.video-button{
		height: 10%;
	}
	.video-download-button{
		width: 100%;
	}
	.video-download-button button{
		color: #FFFFFF;
		background-color: #00AAAA;
		height: 100%;
		font-size: 24rpx;
	}
</style>
