<template>
    <div class="job-history">
        <div class="job-entry" v-for="job in jobs" :key="job.id">
            <h2 class="green bold">{{ job.title }}</h2>
            <h3 class="green">{{ job.company }}</h3>
            <p>{{ job.dates }}</p>
            <ul>
                <li v-for="line in job.description.split('\n').filter(line => line.trim() !== '')" :key="line">{{ line }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Experience',
    data() {
        return {
            jobs: [
                {
                    id: 1,
                    title: 'Software Engineer',
                    company: 'CardFree Inc',
                    dates: 'Feb 2024 - Jan 2025',
                    description: 'Build and optimized C# RESTful APIs for mobile applications and web services. Managed and maintained MySql databases. Handled feature requests, trouble shooting, log analysis and documentation.'
                },
                {
                    id: 2,
                    title: 'Software Developer',
                    company: 'Ekaria LLC',
                    dates: 'Jan 2018 - Dec 2023',
                    description: `
                        Full-Stack Development – Built and maintained front-end, middle-tier, and database components for American Express' Shop with Membership Rewards portal. Led feature development, testing, and deployments, monitored service logs, and handled pager duty for outages.
                        Affiliate Marketing Integrations – Developed .NET C# automation tools for commission reconciliation, integrating with Impact Radius, Commission Junction, Rakuten Advertising, AWIN, Partnerize, Pepperjam, and Ascend. Built internal tools for order and payment tracking.
                        Automated Order Processing – Debugged merchant websites and developed Java-based web scraping solutions for automated order placement.
                        Search Optimization – Migrated search architecture to ElasticSearch, designing SQL Server schemas, stored procedures, and ETL pipelines to process 60K+ search suggestions daily.
                        Accessibility & Compliance – Implemented ADA & WCAG compliance solutions, conducted accessibility assessments, and tested with NVDA, VoiceOver, and TalkBack, ensuring standards using Deque scans.
                        Infrastructure & Performance Optimization – Created PowerShell scripts for automated Windows Server 2019 configuration. Optimized a 50GB+ product catalog (4M+ products) by consolidating servers using SQL Server Synonyms, reducing resource usage.
                        E-commerce & Merchandising – Developed and deployed e-commerce merchandising tools, collaborating with marketing teams on feature enhancements, scoping mockups, and delivering improvements across development, staging, and production environments.
                    `
                },
                {
                    id: 3,
                    title: 'Operation Specialist',
                    company: 'Ekaria LLC',
                    dates: 'Oct 2013 - Jan 2018',
                    description: ''
                }
            ]
        };
    }
};
</script>

<style scoped>
.job-history {
    padding: 20px;
}

.job-entry {
    margin-bottom: 20px;
}

.job-entry h2 {
    margin: 0;
}

.job-entry h3 {
    margin: 5px 0;
}

.job-entry p {
    margin: 5px 0;
}
</style>