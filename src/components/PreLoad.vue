<template>
	<div class="preload" v-if="showThis">
		<img src="../assets/preload_pc.png" />
		<img src="../assets/preload_h5.png" />
		<div class="circle-box">
			<div class="circle-loader-wrap">
				<div class="left-wrap">
					<div class="loader"></div>
				</div>
				<div class="right-wrap">
					<div class="loader"></div>
				</div>
			</div>
		</div>
		<p>檢測進行中，倒數3秒</p>
		<div class="btn-next" @click="doNext()">直接訪問</div>
		<div class="white-bg"></div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			showThis: true,
			timer: null,
			time: 3
		}
	},
	methods: {
		doNext() {
			setInterval(() => {
				this.showThis = false;
			}, 500)
		},
		countdown() {
			this.time--;
			if (this.time == 0) {
				this.showThis = false;
				clearInterval(this.timer)
			}
		}
	},
	mounted() {
		this.timer = setInterval(this.countdown, 1000);
	},
	beforeUnmount() {
		clearInterval(this.timer);
	}
}
</script>

<style>
.preload {
	width: 100vw;
	height: 115vh;
	position: fixed;
	top: 0;
	left: 0;
	background: #fff;
	z-index: 9999;
	color: #343434;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-flow: column;
	font-size: 1.5rem;
	margin-top: -15vh;
	overflow: hidden;
}

.preload>p {
	padding-top: 42rem;
	margin-bottom: 0;
}


.preload img {
	width: 23rem;
	display: none;
	position: absolute;
}

.preload img:first-child {
	display: block;
}

.preload .circle-box {
	width: 28rem;
	height: 28rem;
	margin: 0 auto;
	position: absolute;
	z-index: -1;
	transform: scaleX(-1);
}

.preload .circle-box .circle-loader-wrap {
	overflow: hidden;
	position: relative;
	width: 28rem;
	height: 28rem;
	background-color: #f5f5f5;
	border-radius: 50%;
	transform: rotate(180deg);
}

.preload .circle-box .circle-loader-wrap:after {
	content: '';
	position: absolute;
	left: 1.5rem;
    top: 1.5rem;
    width: 25rem;
    height: 25rem;
	border-radius: 50%;
	background-color: #fff;
}

.preload .circle-box .circle-loader-wrap div {
	overflow: hidden;
	position: absolute;
	width: 50%;
	height: 100%;
}

.preload .circle-box .circle-loader-wrap .loader {
	position: absolute;
	left: 100%;
	top: 0;
	width: 100%;
	height: 100%;
	background-color: #0cacf7;
}

.preload .circle-box .circle-loader-wrap .left-wrap {
	left: 0;
}

.preload .circle-box .circle-loader-wrap .left-wrap .loader {
	border-top-left-radius: 0;
	border-bottom-left-radius: 0;
	transform-origin: 0 50% 0;
	animation: loading-left 3s infinite linear;
}

.preload .circle-box .circle-loader-wrap .right-wrap {
	left: 50%;
}

.preload .circle-box .circle-loader-wrap .right-wrap .loader {
	left: -100%;
	border-bottom-right-radius: 0;
	border-top-right-radius: 0;
	transform-origin: 100% 50% 0;
	animation: loading-right 3s infinite linear;
}

@keyframes loading-left {
	0% {
		transform: rotate(0deg);
	}

	25% {
		transform: rotate(180deg);
	}

	50% {
		transform: rotate(180deg);
	}

	75% {
		transform: rotate(180deg);
	}

	100% {
		transform: rotate(180deg);
	}
}

@keyframes loading-right {
	0% {
		transform: rotate(0deg);
	}

	25% {
		transform: rotate(0deg);
	}

	50% {
		transform: rotate(180deg);
	}

	75% {
		transform: rotate(180deg);
	}

	100% {
		transform: rotate(180deg);
	}
}

.preload .btn-next {
	margin: 1rem auto;
	text-align: center;
	width: 20rem;
	line-height: 2;
	font-size: 2.5rem;
	color: #fff;
	padding-right: 50px;
	font-weight: 600;
	background-repeat: no-repeat;
	background-position: center;
	background-size: contain;
	background-image: url(../assets/btn_next.png);
	cursor: pointer;
}


.preload .btn-next:hover {
	background-image: url(../assets/btn_next_h.png);
}

.preload .btn-next>span {
	color: #fff500;
}

.preload .white-bg {
	width: 100vw;
	height: 100vh;
	position: fixed;
	top: 0;
	left: 0;
	background: #fff;
	display: none;
}

@media only screen and (max-width: 480px) {
	.preload>p {
		padding-top: 32rem;
	}

	.preload {
		font-size: 1.5rem;
	}

	.preload .btn-next {
		font-size: 2rem;
		width: 18rem;
	}
	.preload img:first-child {
		display: none;
	}
	.preload img:nth-child(2) {
		display: block;
		width: 26%;
	}

	.preload .circle-box {
		width: 20rem;
		height: 20rem;
	}

	.preload .circle-box .circle-loader-wrap {
		width: 20rem;
		height: 20rem;
		margin-top: 0px;
	}

	.preload .circle-box .circle-loader-wrap:after {
		left: 1rem;
		top: 1rem;
		width: 18rem;
		height: 18rem;
	}
}
</style>