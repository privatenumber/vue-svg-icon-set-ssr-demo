<template>
	<table>
		<tbody>
			<tr
				v-for="(icon, name) in icons"
			>
				<td>
					{{ name }}
				</td>
				<td>
					<component :is="icon" />
				</td>
			</tr>
		</tbody>
	</table>
</template>

<script>
const requireIcons = require.context('vue-feather-icon-set/icons', false, /\.js$/);

const icons = {};

requireIcons.keys().forEach((iconPath) => {
	icons[iconPath] = requireIcons(iconPath).default;
});

export default {
	data() {
		return {
			icons
		};
	}
}
</script>
