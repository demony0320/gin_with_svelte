<script>
	import { Link } from "svelte-navigator";

	export let to = "";

	// eslint-disable-next-line no-unused-vars
	function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
		const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;
		console.log(location, href, isPartiallyCurrent, isCurrent, isActive);
		//isPartiallyCurrent is /user/list
		// The object returned here is spread on the anchor element's attributes
		if (isActive) {
			return { class: "active" };
		}
		return {};
	}
</script>

<Link {to} {getProps}>
	<slot />
</Link>