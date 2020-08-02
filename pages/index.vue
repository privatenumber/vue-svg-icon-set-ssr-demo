<template>
	<div>
		<label>
			<input
				v-model="renderIcons"
				type="checkbox"
			/>
			Render icons
		</label>
		<table v-if="renderIcons">
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
	</div>
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
			renderIcons: true,
			icons,
		};
	},
};
</script>
