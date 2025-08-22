<script>
  import { MapPin, Phone, Mail, Send } from 'lucide-svelte';
  export let content;
  
  let formData = {
    name: '',
    email: '',
    phone: '',
    message: ''
  };
  
  function handleSubmit(e) {
    e.preventDefault();
    console.log('Form submitted:', formData);
    alert('Thank you for your message! We will get back to you soon.');
    formData = { name: '', email: '', phone: '', message: '' };
  }
</script>

<section id="contact" class="section bg-secondary">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{content.contact.title}</h2>
      <p class="section-subtitle">{content.contact.subtitle}</p>
    </div>
    
    <div class="contact-grid">
      <div class="contact-info animate-slideInLeft">
        <div class="info-item">
          <div class="info-icon">
            <MapPin size={24} />
          </div>
          <div class="info-content">
            <h4 class="info-title">Visit Our Office</h4>
            <p class="info-text text-secondary">{content.company.address}</p>
          </div>
        </div>
        
        <div class="info-item">
          <div class="info-icon">
            <Phone size={24} />
          </div>
          <div class="info-content">
            <h4 class="info-title">Call Us</h4>
            <p class="info-text text-secondary">{content.company.phone}</p>
          </div>
        </div>
        
        <div class="info-item">
          <div class="info-icon">
            <Mail size={24} />
          </div>
          <div class="info-content">
            <h4 class="info-title">Email Us</h4>
            <p class="info-text text-secondary">{content.company.email}</p>
          </div>
        </div>
        
        <div class="map-container rounded-xl shadow-lg">
          <iframe 
            title="Office Location"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d193595.25299748826!2d-74.11976389828391!3d40.69766374859258!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x89c24fa5d33f083b%3A0xc80b8f06e177fe62!2sNew%20York%2C%20NY%2C%20USA!5e0!3m2!1sen!2s!4v1644262070741!5m2!1sen!2s"
            width="100%"
            height="250"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
            class="rounded-xl">
          </iframe>
        </div>
      </div>
      
      <div class="contact-form-container card shadow-xl animate-slideInRight">
        <form on:submit={handleSubmit} class="contact-form">
          <div class="form-group">
            <label for="name" class="form-label">Full Name</label>
            <input 
              id="name"
              type="text" 
              placeholder={content.contact.form.namePlaceholder}
              bind:value={formData.name}
              required
              class="form-input"
            />
          </div>
          
          <div class="form-row">
            <div class="form-group">
              <label for="email" class="form-label">Email Address</label>
              <input 
                id="email"
                type="email" 
                placeholder={content.contact.form.emailPlaceholder}
                bind:value={formData.email}
                required
                class="form-input"
              />
            </div>
            
            <div class="form-group">
              <label for="phone" class="form-label">Phone Number</label>
              <input 
                id="phone"
                type="tel" 
                placeholder={content.contact.form.phonePlaceholder}
                bind:value={formData.phone}
                class="form-input"
              />
            </div>
          </div>
          
          <div class="form-group">
            <label for="message" class="form-label">Message</label>
            <textarea 
              id="message"
              placeholder={content.contact.form.messagePlaceholder}
              bind:value={formData.message}
              required
              rows="6"
              class="form-textarea"
            ></textarea>
          </div>
          
          <button type="submit" class="btn btn-primary btn-lg btn-icon">
            <Send size={20} />
            {content.contact.form.submitButton}
          </button>
        </form>
      </div>
    </div>
  </div>
</section>

<style>
  .contact-grid {
    display: grid;
    gap: var(--space-4xl);
    align-items: start;
  }

  @media (min-width: 1024px) {
    .contact-grid {
      grid-template-columns: 0.9fr 1.1fr;
      gap: var(--space-3xl);
    }
  }

  .contact-info {
    display: flex;
    flex-direction: column;
    gap: var(--space-xl);
  }

  .info-item {
    display: flex;
    gap: var(--space-lg);
    padding: var(--space-xl);
    background: var(--bg-primary);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
    transition: all var(--transition-base);
  }

  .info-item:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
    border-color: var(--primary-color);
  }

  .info-icon {
    flex-shrink: 0;
    width: 3.5rem;
    height: 3.5rem;
    background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-dark) 100%);
    border-radius: var(--radius-lg);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    box-shadow: var(--shadow-md);
    transition: all var(--transition-base);
  }

  .info-item:hover .info-icon {
    transform: scale(1.1) rotate(5deg);
    box-shadow: var(--shadow-lg);
  }

  .info-content {
    flex: 1;
  }

  .info-title {
    font-size: 1.125rem;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: var(--space-xs);
  }

  .info-text {
    font-size: 0.95rem;
    line-height: 1.6;
  }

  .map-container {
    margin-top: var(--space-xl);
    overflow: hidden;
    transition: all var(--transition-base);
  }

  .map-container:hover {
    transform: scale(1.02);
  }

  .contact-form-container {
    padding: var(--space-2xl);
    background: var(--bg-primary);
    border: 1px solid var(--border-light);
    position: relative;
    overflow: hidden;
  }

  .contact-form-container::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
  }

  .contact-form {
    position: relative;
    z-index: 1;
  }

  .form-row {
    display: grid;
    gap: var(--space-lg);
  }

  @media (min-width: 768px) {
    .form-row {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .form-row .form-group {
    margin-bottom: 0;
  }

  /* Enhanced form styling */
  .form-input:focus,
  .form-textarea:focus {
    transform: translateY(-2px);
    box-shadow: var(--shadow-lg), 0 0 0 3px rgba(37, 99, 235, 0.1);
  }

  /* Submit button full width on mobile */
  .contact-form .btn {
    width: 100%;
  }

  @media (min-width: 640px) {
    .contact-form .btn {
      width: auto;
      min-width: 12rem;
    }
  }

  /* Animation delays */
  .info-item:nth-child(1) { animation-delay: 0.1s; }
  .info-item:nth-child(2) { animation-delay: 0.2s; }
  .info-item:nth-child(3) { animation-delay: 0.3s; }
  .map-container { animation-delay: 0.4s; }

  /* Mobile responsive adjustments */
  @media (max-width: 768px) {
    .contact-form-container {
      padding: var(--space-xl);
    }

    .info-item {
      padding: var(--space-lg);
      flex-direction: column;
      text-align: center;
    }

    .info-icon {
      width: 3rem;
      height: 3rem;
      margin: 0 auto;
    }

    .form-row {
      grid-template-columns: 1fr;
      gap: 0;
    }

    .form-row .form-group {
      margin-bottom: var(--space-lg);
    }
  }
</style>