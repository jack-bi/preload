<template>
	<HomePage />
	<PreLoad />

</template>

<script>
import HomePage from './components/HomePage'
import PreLoad from '@/components/PreLoad'

export default {
	name: 'App',
	components: {
		HomePage,
		PreLoad,
	}
}
</script>
