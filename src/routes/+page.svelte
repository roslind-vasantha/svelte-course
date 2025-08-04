<script lang="ts">
	const target = {
		firstName: 'Roslind',
		lastName: 'Vasantha',
		occupations: [],

		get fullName() {
			return `${this.firstName} ${this.lastName}`;
		},

		set occupation(value: string) {
			console.log(`Adding ${value} to occupations`);
			this.occupations.push(value);
		}
	};

	// target.firstName = 'Afroze';
	// console.log(target.fullName);

	target.occupation = 'Web dev';
	console.log(target);

	const handler = {
		get(target, prop) {
			// console.log(target, prop);
			// return 'Hello';
			return prop in target ? target[prop] : 'NA';
		},

		set(target, prop, value) {
			console.log(`Setting; ${prop} = ${value}`);

			if (['firstName', 'lastName'].includes(prop)) {
				if (typeof value !== 'string') {
					throw new TypeError(`Property ${prop} must be a string.`);
				}
			}

			target[prop] = value;
			return true;
		}
	};

	const proxy = new Proxy(target, handler);

	proxy.firstName = 'Zubae';
	// proxy.lastName = 2;
	console.log(proxy.firstName);
</script>

<style>
	:global(body) {
		background-color: #222;
	}
</style>
