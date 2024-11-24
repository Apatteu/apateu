<script>
	import "../app.css";

	let isMenuOpen = false;

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@100;400;700&display=swap" rel="stylesheet">
</svelte:head>

<div class="navbar">
	<a href="/" class="mr-auto font-bold logo">Apateu</a>
	<button class="burger" on:click={toggleMenu} aria-label="Toggle navigation" aria-expanded={isMenuOpen}>
		<div class="line"></div>
		<div class="line"></div>
		<div class="line"></div>
	</button>
	<div class={`navbar-links ${isMenuOpen ? 'open' : ''}`}>
		<a href="/apartment">Apartment</a>
		<a href="/about">About</a>
		<a href="/contact">Contact</a>
	</div>
</div>

<main class="main-content">
	<slot></slot>
</main>

<style>
	:global(body) {
		font-family: 'Poppins', sans-serif;
		margin: 0;
		padding: 0;
		background-color: #DBDBDB;
		background-image: url('/image/background.png'); /* Replace with your image path */
		background-size: 125%; /* Reduced size of the background image to 80% */
		background-position: center -150px; /* Move the image upwards to raise it */
		background-repeat: no-repeat; /* Prevent the image from repeating */
		background-attachment: fixed; /* Keeps the image fixed while scrolling */
		display: flex;
		flex-direction: column; /* Allow for vertical stacking of elements */
		min-height: 100vh; /* Full viewport height */
	}

	/* Navbar styles */
	.navbar {
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		background-color: #515739;
		padding: 0.5rem 1.5rem; /* Reduced padding */
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		width: 100%; /* Ensure navbar spans full width */
		position: relative; /* To position the burger in relation to the navbar */
	}

	.navbar a {
		color: #ffffff;
		text-decoration: none;
		padding: 0.25rem 0.75rem; /* Reduced padding for links */
		font-size: 0.9rem; /* Reduced font size */
		transition: transform 0.2s, color 0.2s;
		border-radius: 5px;
	}

	.navbar .logo {
		font-size: 1.2rem; /* Reduced font size */
		font-weight: bold;
		transition: transform 0.2s, color 0.2s;
	}

	.navbar a:hover {
		color: #DF6630;
		transform: scale(1.1);
	}

	.burger {
		display: none;
		flex-direction: column;
		cursor: pointer;
		background: none;
		border: none;
		position: absolute; /* Positioning burger relative to navbar */
		top: 0.5rem; /* Slightly from the top */
		right: 1.5rem; /* Slightly from the right */
	}

	.line {
		width: 20px; /* Reduced width */
		height: 2px; /* Reduced height */
		background-color: #ffffff;
		margin: 3px 0; /* Reduced margin */
		transition: 0.3s;
	}

	/* Main content styles */
	.main-content {
		flex: 1; /* This ensures the content takes up the remaining space */
		padding: 2rem;
		display: flex;
		flex-direction: column; /* Allows content to stack vertically */
		justify-content: center; /* Centers content vertically */
	}

	/* Responsive styles */
	@media (max-width: 768px) {
		.navbar {
			flex-direction: column;
			align-items: flex-start;
		}

		/* Ensure burger appears on the top right corner */
		.burger {
			display: flex; /* Show burger in mobile view */
			top: 1rem; /* Adjust top position */
			right: 1.5rem; /* Adjust right position */
		}

		.navbar-links {
			display: none;
			flex-direction: column;
			width: 100%;
		}

		.navbar-links.open {
			display: flex;
		}

		.navbar a {
			width: 100%;
			text-align: left;
			padding: 1rem;
		}
	}

	@media (max-width: 480px) {
		.navbar .logo {
			font-size: 1.1rem; /* Further reduced logo size */
		}

		.main-content {
			padding: 1rem;
		}
	}
</style>
