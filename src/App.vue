<script>
import Header from './components/Header.vue'
import Aside from './components/Aside.vue'
import Dashboard from './components/Dashboard.vue'
import Footer from './components/Footer.vue'

export default {
	components: {
		Header,
		Aside,
		Dashboard,
		Footer,
	},
	data() {
		return {
			mediaPlanes: [],
			reports: [],
		}
	},
	methods: {
		addMediaPlane() {
			const id = this.mediaPlanes.length + 1
			const length = this.mediaPlanes.length

			const mediaPlane = {
				id: this.mediaPlanes.length + 1,
				title: `Companyname ${id}/`,
				status: 'loading',
			}

			if (length) {
				this.mediaPlanes.forEach(item => (item.status = 'done'))
				this.mediaPlanes[length - 1].status = 'completed'
			}

			this.mediaPlanes.push(mediaPlane)
		},
		addReport() {
			const id = this.reports.length + 1
			const length = this.reports.length

			const report = {
				id: this.reports.length + 1,
				title: `Companyname ${id}/`,
				status: 'loading',
			}

			if (length) {
				this.reports.forEach(item => (item.status = 'done'))
				this.reports[length - 1].status = 'completed'
			}

			this.reports.push(report)
		},
	},
}
</script>

<template>
	<div class="page">
		<Header></Header>
		<section class="section">
			<div class="container">
				<Aside :mediaPlanes="mediaPlanes" :reports="reports"></Aside>
				<Dashboard
					:mediaPlanes="mediaPlanes"
					:reports="reports"
					@add-media="addMediaPlane"
					@add-report="addReport"
				></Dashboard>
			</div>
		</section>
		<Footer></Footer>
	</div>
</template>

<style scoped lang="scss">
.page {
	display: grid;
	grid-template-columns: 295px 1fr;
	grid-template-rows: auto 1fr auto;
	min-height: 100vh;
	margin: 0 auto;
}

.section {
	grid-column: 1/3;
	height: 100%;
	& .container {
		display: grid;
		grid-template-columns: 1fr;
		height: inherit;
	}
}

@media (min-width: $media-md) {
	.section {
		& .container {
			row-gap: 20px;
		}
	}
}

@media (min-width: 1200px) {
	.section {
		& .container {
			grid-template-columns: 295px 1fr;
			column-gap: 30px;
			row-gap: 20px;
			padding-bottom: 60px;
		}
	}
}
</style>
