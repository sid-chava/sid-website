

<script>
	let expandedProject = null;
  
	const projects = [
	  {
		title: "Hathora Investment Memo",
		description: "As part of NYU SVS, my team was tasked by MaC Venture Capital to source a early-stage opportunity that was providing cloud-infrastructure for games. During our search, I ended up at a NY Tech Week Happy Hour event, where I was introduced to the founder of Hathora, Siddharth Dhulipalla and the rest of the team. After an extremely eye-opening converstation, I brought additional research to rest of my team and MaC, who gave the greenlight to proceed with the memo. As we engaged in discussion with the MaC team as we continued developing our thesis, we became more and more convinced that we had a winner on our hands. Our final thesis was ultimately presented to a several members of the MaC Venture Capital team.",
		imageUrl: "/Images/Hathora.png",
		link: "https://strategic-venture-society.notion.site/Hathora-Investment-Memorandum-1dd8554d3a5946efbdc892dd3ffc12c8?pvs=4"
	  },
	  {
		title: "Mobileye IPO Analysis",
		description: "Mobileye, a leader in the advanced driver assistance system (ADAS) market, filed an S1 during early fall of 2022. As part of NYU SVS, I was asked to methodically review the filing in order to generate analysis and recommendations for the pending IPO. As part of my research, I deeply immersed myself in learning the key differences between Mobileye and other competitors, such as Tesla, Cruise, Waymo, and more in order to determine its position within the competitive landscape. After review, I was confident that Mobileye's upside was worth investing in. Mobileye (MBLY) increased by 31.22% in its first year of listing.",
		imageUrl: "/Images/Mobileye.png",
		link: "https://drive.google.com/file/d/1S_PoDL4pP_6Zc9a0yH28J-0BqMHc4Cds/view?usp=sharing"
	  },
	  {
		title: "Commons Investment Pitch",
		description: "As part of NYUVC, an annual venture capital pitch competition, my team was tasked with sourcing an early-stage investment opportunity within the ClimateTech space. Commons stood out to me as the most innovative consumer focused carbon-tracking startup. Common's key value lies within its tracking of indirect emmissions through spending, and offers carefully vetted carbon offsets. After reading more about the app and the team behind it, my team and I put together a thesis and worked out a valuation for the company. We then compiled a deck which was presented to VC judges from General Atlantic, Sequoia Capital, and more, ending tied for third place.",
		imageUrl: "/Images/joro.png",
		link: "https://drive.google.com/file/d/1X5RSGJNZb3TzG0pLAweenjVGqPWAs8pd/view?usp=sharing"
	  },
	
	  {
		title: "Tachyon Competitive Analysis",
		description: "As part of NYU SVS, my team was tasked by Consensys Mesh to evaluate the competitive landscape of Web3 accelerators, and offering recommendations to improve positioning for its Tachyon accelerator. My team spent several weeks scraping data from Pitchbook, X, and more in order to quantitatively evaluate the performance and positioning of each accelerator. As we analyzed the data we scaped, we worked with a partner at Mesh in order to understand what insights our data was presenting. We then compiled our findings into a pitch deck and presented it to the Mesh leadership team. Following the presentation, the team invited me to intern for the firm in the summer which I accepted.",
		imageUrl: "/Images/ConsensysMesh.png",
		link: "https://drive.google.com/file/d/1eoI_KR5bQ9-r8PuhCiKr5fNTX9-HHuGg/view?usp=sharing"
	  }
	  // ... Add more projects as needed
	];
	function toggleProject(project) {
  // If the clicked project is already expanded, collapse it
  if (expandedProject === project) {
    expandedProject = null;
  } else {
    // Otherwise, expand the clicked project and collapse others
    expandedProject = project;
  }

  // Update the max-height for all project details
  updateProjectDetailsHeight();
}

function updateProjectDetailsHeight() {
  const detailsElements = document.querySelectorAll('.project-details');
  detailsElements.forEach(el => {
    // Check if el is an HTMLElement
    if (el instanceof HTMLElement) {
      if (el.parentElement.querySelector('.project') === expandedProject) {
        el.style.maxHeight = el.scrollHeight + 'px';
      } else {
        el.style.maxHeight = null;
      }
    }
  });
}
  function handleKeydown(event, project) {
    if (event.key === 'Enter') {
      toggleProject(project);
    }
  }
    // Smooth scroll action
	function smoothScroll(node) {
    node.addEventListener('click', event => {
      // Prevent default anchor behavior
      event.preventDefault();

      // Extract the target element's id from the href attribute
      const targetId = node.getAttribute('href').substring(1);
      const targetElement = document.getElementById(targetId);

      // Scroll to the target element smoothly
      if (targetElement) {
        targetElement.scrollIntoView({
          behavior: 'smooth'
        });
      }
    });

    return {
      destroy() {
        node.removeEventListener('click', event);
      }
    };
  }
  </script>
 <main>
	<!-- Header section with navigation and personal details -->
	<header>
	  <name>Siddarth Chava</name>
	  <nav id="navbar">
		<ul>
		  <li><a href="#about" use:smoothScroll>About</a></li>
		  <li><a href="https://drive.google.com/file/d/179UDRaI889V_sKVV7xhqBzMhCjSK7gl7/view?usp=sharing">Resume</a></li>
		  <!-- Links to LinkedIn, GitHub, and Email with respective icons -->
		  <li><a href="https://www.linkedin.com/in/sid-chava-19066a232/" target="_blank"><img src="/Images/linkedin.png" alt="LinkedIn"></a></li>
		  <li><a href="https://github.com/sid-chava" target="_blank"><img src="/Images/github.png" alt="GitHub"></a></li>
		  <li><a href="mailto:siddarth.chava@stern.nyu.edu"><img src="/Images/email.png" alt="Email"></a></li>
		</ul>
	  </nav>
	</header>
  
	<!-- Introduction section with personal statement -->
	<section id="intro">
	  <div class="h3">
		<h3>Hi! I'm a product/growth engineer dedicated to designing intelligent systems.</h3>
		<!-- Previous experiences -->
		<br><br>
		</div>
		<div class="h10">
			<h10>Here is some of my recent work:</h10>
			</div>
	</section>
  
	<!-- Projects section with Swiper carousel -->
	<section id="projects" class="grid-layout">
		{#each projects as project}
			<div class="project-container">
				<div class="project" on:click={() => toggleProject(project)}>
					<img src={project.imageUrl} alt={project.title} class="project-image" />
					<div class={expandedProject === project ? 'project-overlay hidden' : 'project-overlay'}>
						{project.title}
					</div>
				</div>
				<div class={expandedProject === project ? 'project-details active' : 'project-details'}>
					<p>{project.description}</p>
					<a href={project.link} target="_blank" class="project-link">View Full Project</a>
				</div>
			</div>
		{/each}
	</section>
	<section id="about">
		<header>
			<h2>About Me</h2>
		</header>
		<p>
			<!-- Your about paragraph text goes here -->
			Hello! My name is Sid and I am a sophomore at NYU double majoring in computer science and business. Previously, I've work as Growth @ DECKO, and Operations @ Consensys Mesh. Currently, I'm Post-Mentorship Lead for NYU Strategic Venture Society (NYU Stern's premier venture capital and tech club), where I provide advisory, research, diligence, and sourcing services to venture firms. Fast-paced environments and multi-disciplinary roles are where I thrive. I'm also learning software development - my first project is this website! When I have free time, I enjoy visiting art galleries around NYC, watching the Portland Trailblazers (my hometown team), or playing playing poker with friends. 
			<br>
			<br>
			I'm always looking for opportunities to learn, grow, and build. Feel free to reach out and let's chat!
		</p>
	</section>
	<footer>
		<div class="footer-left">
		  Siddarth Chava @ 2024
		</div>
		<nav class="footer-right">
		  <ul>
			<li><a href="#intro" use:smoothScroll>Work</a></li>
			<li><a href="https://drive.google.com/file/d/179UDRaI889V_sKVV7xhqBzMhCjSK7gl7/view?usp=sharing">Resume</a></li>
			<li><a href="https://www.linkedin.com/in/sid-chava-19066a232/" target="_blank"><img src="/Images/linkedin.png" alt="LinkedIn"></a></li>
			<li><a href="https://github.com/your-github/" target="_blank"><img src="/Images/github.png" alt="GitHub"></a></li>
			<li><a href="mailto:siddarth.chava@stern.nyu.edu"><img src="/Images/email.png" alt="Email"></a></li>
		  </ul>
		</nav>
	  </footer>
	</main>

  <style>
	/* Header styles */

	main {
    background: 
        repeating-linear-gradient(
            to right, 
            rgba(48, 60, 60, 0.078), /* Line color */
            rgba(58, 58, 58, 0) 2px, /* Line thickness */
            transparent 2px,
            transparent 12.5% /* Spacing between lines */
        ),
        radial-gradient(#e2e2e2, #eaeaea); /* Base background */
    box-shadow: inset 0 0 100px rgba(255, 254, 254, 0.5); /* Inner shadow for depth */
    padding: 0 35px; /* Padding on both left and right sides */
    background-size: auto, cover; /* Auto for line spacing, cover for base gradient */
}
main::before, main::after {
    content: '';
    position: absolute;
    height: 100%;
    width: 10px; /* Width of the decorative area */
    top: 0;
    background-image: 
        repeating-linear-gradient(
            to bottom,
            transparent,
            transparent 30px, /* Random spacing */
            rgba(48, 60, 60, 0.078) 30px, /* Dot color */
            rgba(48, 60, 60, 0.078) 32px, /* Dot size */
            transparent 32px,
            transparent 100px /* More random spacing */
        ),
        repeating-linear-gradient(
            to bottom,
            transparent,
            transparent 45px, /* Random spacing for pluses */
            rgba(48, 60, 60, 0.078) 45px,
            rgba(48, 60, 60, 0.078) 47px, /* Horizontal line of plus */
            transparent 47px,
            transparent 55px,
            rgba(48, 60, 60, 0.078) 55px,
            rgba(48, 60, 60, 0.078) 57px, /* Vertical line of plus */
            transparent 57px
        );
    background-size: 100% 200px, 100% 100px; /* Different sizes for each pattern */
}

main::before {
    left: 0;
}

main::after {
    right: 0;
}
	


	header {
	  display: flex;
	  align-items: center;
	  justify-content: space-between;
	  padding-top: 1em;
	  margin: 0 auto;
	  margin-bottom: 30px;
	}
  
	/* Name styling */
	name {
    font-family: 'TT Interphases W05 Medium';
	  color: black;
	  font-size: 1.8rem;
	  margin: 0;
	  font-weight: bolder;
	  text-align: left;
	}
  
	/* Navigation bar styling */
	#navbar {
    font-family: 'TT Interphases W05 Regular';
	  display: flex;
	  list-style: none;
	  margin: 0;
	  padding: 0;
	}
  
	#navbar ul {
	  display: flex;
	  align-items: center;
	  list-style-type: none;
	}
  
	#navbar li {
	  padding: 0 20px;
	}
  
	#navbar a {
	  text-decoration: none;
	  color: black;
	}
  
	#navbar a img {
	  width: 20px;
	  height: 20px;
	  vertical-align: middle;
	}
  
	/* Introduction section styling */
	#intro {
    font-family: 'TT Interphases W05 Medium';
	  padding-top: 90px;
	  padding-right: 30%;
	  text-align: left;
    font-weight: bolder;
	  padding-bottom: 30px;

	}
  
	.h3 h3 {
	  color: #0019a8;
	  font-size: 3rem;
    font-weight: light;
	  padding-bottom: 60px;
	}

	.h10 h10 {
    font-family: 'TT Interphases W05 Regular';
		color: black;
		font-size: 1.4rem;
	}
  
  
	
  
	/* Project section styles */
	#projects {
		column-count: 2; /* Default to two columns */
		column-gap: 40px;
	}

	.project-container {
		break-inside: avoid; /* Prevents the project from being split across columns */
		margin-bottom: 20px; /* Space between projects */
		position: relative; /* For absolute positioning of details */
	}
	.project {
		margin-bottom: 20px;
		position: relative; /* Needed for positioning the overlay */
		cursor: pointer;
	}

	.project-image {
		width: 100%; /* Full width of the container */
		height: auto;
		display: block;
		cursor: pointer;
	}
	.project-overlay {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(36, 36, 36, 0.8); /* Light grey background */
		color: white;
		font-size: 1.4rem;
		display: flex;
		align-items: center;
		justify-content: center;
		opacity: 0;
		transition: opacity 0.3s ease;
		cursor: pointer;
	}
	*, *::before, *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box; /* Includes padding and border in the element's total width and height */
}

	.project:hover .project-overlay {
		opacity: 1; /* Show overlay on hover */
	}
	.hidden {
  		display: none; /* Hide overlay when project details are expanded */
	}

	.project-details {
		max-height: 0;
		overflow: hidden;
		transition: max-height 0.3s ease-out, padding 0.3s ease-out;
		position: relative;
		z-index: 1;
    text-align: left;
    color: black;
		background: #f9f9f9;
		padding: 0 15px;
	}
	.project-details.active {
		max-height: 500px; /* or enough to accommodate the content */
		padding: 15px; /* Add padding when expanded for better readability */
	}	

	.project-link {
		display: inline-block;
		margin-top: 10px;
		color: #007bff;
		text-decoration: none;
	}
	#about {
		padding-top: 20px;
		padding-bottom:20px;
    text-align: left;
	}

	#about header h2 {
    font-family: 'TT Interphases W05 DemiBold';
		color: #0019a8; /* Adjust the color as needed */
		font-size: 2.5rem; /* Adjust font size as needed */
		margin-bottom: 10px; /* Space between header and paragraph */
	}

	#about p {
		font-size: 1rem; /* Adjust font size as needed */
		color: #333; /* Adjust text color as needed */
		line-height: 1.6; /* Adjust line height for better readability */
		/* Additional paragraph styling if needed */
	}
	footer {
    font-family: 'TT Interphases W05 Regular';
    display: flex;
    justify-content: space-between;
    align-items: center;
	padding-top: 50px;
	padding-bottom: 10px;

  }

  .footer-left {
	padding-left: 0;
    font-size: 1rem;
    color: #333;
  }

  .footer-right {
    font-family: 'TT Interphases W05 Regular';
    display: flex;
    align-items: center;
  }

  .footer-right ul {
    display: flex;
    list-style-type: none;
    margin: 0;
  }

  .footer-right li {
    padding: 0 20px;
  }

  .footer-right a {
    text-decoration: none;
    color: black;
  }

  .footer-right a img {
    width: 20px;
    height: 20px;
    vertical-align: middle;
  }


	/* Responsive design for header */
	@media (max-width: 750px) {
	  header {
		max-width: none;
	  }
	  #projects {
    	column-count: 1;
  	}
	  header {
    flex-direction: column;
    align-items: center;
    padding-top: 0.5em;
  }

  name {
    font-size: 1.2rem; /* Smaller font size for name */
    padding-bottom: 0.5em; /* Space between name and navigation bar */
  }

  #navbar {
    padding: 0;
  }

  #navbar ul {
    justify-content: center;
  }

  #navbar li {
    padding: 0 10px; /* Reduce space between navigation items */
  }

  /* Adjustments for Intro Section */
  #intro {
    padding: 20px 15px; /* Reduce padding */
    text-align: center; /* Center align text */
  }

  .h3 h3, .h10 h10 {
    font-size: 1.8rem; /* Smaller font size for headings */
  }

  /* Adjustments for About Section */
  #about {
    text-align: center; /* Center align text */
    padding: 10px 15px; /* Adjust padding */
  }

  /* Adjustments for Footer */
  footer {
    flex-direction: column;
    text-align: center; /* Center align footer content */
  }

  .footer-right {
    margin-top: 10px;
  }

  .footer-right ul {
    justify-content: center; /* Center align navigation items */
  }
	}
	
  </style>