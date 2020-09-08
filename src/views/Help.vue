<template>
	<section class="tify-help">
		<h2 class="tify-sr-only">{{ 'Help'|trans }}</h2>

		<div class="tify-help_section -doc">
			<h3>{{ 'Documentation'|trans }}</h3>
			<p><a :href="info.DOCS_URL">{{ 'Open documentation'|trans }}</a></p>
		</div>

		<div class="tify-help_section -about">
			<h3>{{ 'About TIFY'|trans }}</h3>
			<p v-html="$root.$options.filters.trans('TIFY is a slim and mobile-friendly IIIF document viewer.')"/>
			<p>
				Version {{ info.VERSION }}
				&middot;
				<a :href="info.REPOSITORY_URL">{{ 'Source code'|trans }}</a>
				&middot;
				<a :href="info.CONTRIBUTORS_URL">{{ 'Contributors'|trans }}</a>
			</p>
			<p v-html="$root.$options.filters.trans(licenseHtml)"/>
			<p v-html="$root.$options.filters.trans(copyrightHtml)"/>
			<p v-html="$root.$options.filters.trans(sponsorHtml)"/>
			<hr>
			<p>
				<a :href="info.BUGS_URL">{{ 'Report a bug'|trans }}</a>
			</p>
		</div>
	</section>
</template>

<script>
export default {
	computed: {
		copyrightHtml() {
			return 'Copyright &copy; 2017-2020'
				+ ' <a href="https://www.uni-goettingen.de/en">Göttingen University</a>'
				+ ' / '
				+ '<a href="https://www.sub.uni-goettingen.de/en/">Göttingen State and University Library</a>';
		},
		licenseHtml() {
			return 'Released under the'
				+ ' <a href="https://github.com/tify-iiif-viewer/tify/blob/main/LICENSE">'
				+ 'GNU Affero General Public License v3.0'
				+ '</a>';
		},
		sponsorHtml() {
			return 'Sponsored by <a href="https://aspectis.net/">Aspectis</a>';
		},
		info() {
			return JSON.parse(unescape(process.env.VUE_APP_INFO));
		},
	},
};
</script>
