<template>
	<div name="show">
		<ul class="goodList">
			<li v-for="good in list">
				<img v-bind:src="good.img" v-bing:alt="good.goodName">
				<p>{{good.goodName}}</p>
			</li>
		</ul>
	</div>
</template>

<script type="text/javascript">
	export default {
		name: "show",
		data() {
			var obj = this;
			var url = "";
			if (obj.goodId == 1) {
				url = "json/bjb.json";
			} else if (obj.goodId == 2) {
				url = "json/shouji.json";
			} else {
				url = "json/bjb.json";
			}
			this.$http.get(url).then(function(res) {
				obj.list = res.data;
			})
			return {
				list: []
			}
		},
		props: {
			goodId: Number
		},
		watch: {
			goodId() {
				var obj = this;
				var url = "";
				if (obj.goodId == 1) {
					url = "json/bjb.json";
				} else if (obj.goodId == 2) {
					url = "json/shouji.json";
				} else {
					url = "json/bjb.json";
				}
				this.$http.get(url).then(function(res) {
					obj.list = res.data;
				})
				return {
					list: []
				}
			}
		},
		methods: {

		}
	}
</script>

<style type="text/css">
	.goodList li {
		width: 200px;
		height: 200px;
		list-style: none;
		float: left;
		font-size: 9px;
		color: red;
		margin-bottom: 30px;
	}

	.goodList img {
		width: 180px;
		height: 180px;
	}
</style>
