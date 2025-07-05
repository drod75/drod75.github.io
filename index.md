---
layout: default
---

<div class="hero min-h-screen bg-base-100">
    <div class="hero-content flex-col lg:flex-row-reverse">
        <img src="{{ site.data.user.picture | relative_url }}" class="max-w-sm rounded-lg shadow-2xl" />
        <div>
            <h1 class="text-5xl font-bold">{{ site.data.user.name }}</h1>
            <p class="py-6">
                {{ site.data.user.email }} | {{ site.data.user.location }}
            </p>
            <a href="{{ site.data.user.website }}" class="btn btn-primary">Website</a>
            <a href="https://{{ site.data.user.linkedin }}" class="btn btn-secondary">LinkedIn</a>
        </div>
    </div>
</div>

<div class="container mx-auto p-8">
    <section id="about" class="py-12">
        <h2 class="text-4xl font-bold text-center mb-8 bg-gradient-to-r from-primary to-accent text-transparent bg-clip-text">About Me</h2>
        <div class="card bg-base-100 shadow-xl">
            <div class="card-body">
                <p class="text-lg">{{ site.data.bio.introduction | markdownify | replace: '<p>', '' | replace: '</p>', '' }}</p>
            </div>
        </div>
    </section>

    <section id="projects" class="py-12">
        <h2 class="text-4xl font-bold text-center mb-8 bg-gradient-to-r from-primary to-accent text-transparent bg-clip-text">Projects</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            {% for project in site.data.projects %}
            <div class="card bg-base-100 shadow-xl image-full">
                <figure><img src="{{ project.image | relative_url }}" alt="{{ project.title }}" /></figure>
                <div class="card-body">
                    <h3 class="card-title">{{ project.title }}</h3>
                    <p class="text-sm">{{ project.date }}</p>
                    <p>{{ project.description }}</p>
                </div>
            </div>
            {% endfor %}
        </div>
    </section>

    <section id="experience" class="py-12">
        <h2 class="text-4xl font-bold text-center mb-8 bg-gradient-to-r from-primary to-accent text-transparent bg-clip-text">Experience</h2>
        {% for experience_type in site.data.experience %}
        <h3 class="text-3xl font-bold mb-6 text-center">{{ experience_type.type }}</h3>
        <div class="space-y-8">
            {% for job in experience_type.jobs %}
            <div class="card card-side bg-base-100 shadow-xl">
                <figure class="p-4 w-1/4"><img src="{{ job.image | relative_url }}" alt="{{ job.company }}" class="object-contain"></figure>
                <div class="card-body w-3/4">
                    <h4 class="card-title">{{ job.title }} at {{ job.company }}</h4>
                    <p class="text-sm text-gray-500">{{ job.location }} | {{ job.dates }}</p>
                    <ul class="list-disc pl-5">
                        {% for item in job.description %}
                        <li>{{ item }}</li>
                        {% endfor %}
                    </ul>
                </div>
            </div>
            {% endfor %}
        </div>
        {% if forloop.last == false %}<div class="divider my-12"></div>{% endif %}
        {% endfor %}
    </section>

    <section id="education" class="py-12">
         <h2 class="text-4xl font-bold text-center mb-8 bg-gradient-to-r from-primary to-accent text-transparent bg-clip-text">Education</h2>
         {% for edu in site.data.education %}
         <div class="card bg-base-100 shadow-xl">
             <div class="card-body">
                 <h3 class="card-title">{{ edu.institution }}</h3>
                 <p><strong>Degree:</strong> {{ edu.degree }}</p>
                 <p><strong>Minor:</strong> {{ edu.minor }}</p>
                 <p><strong>GPA:</strong> {{ edu.gpa }}</p>
                 <p><strong>Expected Graduation:</strong> {{ edu.expected_date }}</p>
                 <p><strong>Location:</strong> {{ edu.location }}</p>
                 <p class="mt-2"><strong>Relevant Coursework:</strong></p>
                 <ul class="list-disc pl-5">
                   {% for course in edu.relevant_coursework %}
                     <li>{{ course }}</li>
                   {% endfor %}
                 </ul>
             </div>
         </div>
         {% endfor %}
     </section>

     <section id="skills" class="py-12">
         <h2 class="text-4xl font-bold text-center mb-8 bg-gradient-to-r from-primary to-accent text-transparent bg-clip-text">Skills</h2>
         <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
           {% for skill in site.data.skills %}
             <div class="card bg-base-100 shadow-xl">
                 <div class="card-body">
                     <h3 class="card-title">{{ skill.category }}</h3>
                     <p>{{ skill.items }}</p>
                 </div>
             </div>
           {% endfor %}
         </div>
     </section>
</div>
