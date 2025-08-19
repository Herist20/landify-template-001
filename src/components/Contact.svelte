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

<section id="contact" class="section">
  <div class="container">
    <h2 class="section-title">{content.contact.title}</h2>
    <p class="section-subtitle">{content.contact.subtitle}</p>
    
    <div class="contact-grid">
      <div class="contact-info">
        <div class="info-card">
          <div class="info-icon">
            <MapPin size={24} />
          </div>
          <div>
            <h4>Visit Our Office</h4>
            <p>{content.company.address}</p>
          </div>
        </div>
        
        <div class="info-card">
          <div class="info-icon">
            <Phone size={24} />
          </div>
          <div>
            <h4>Call Us</h4>
            <p>{content.company.phone}</p>
          </div>
        </div>
        
        <div class="info-card">
          <div class="info-icon">
            <Mail size={24} />
          </div>
          <div>
            <h4>Email Us</h4>
            <p>{content.company.email}</p>
          </div>
        </div>
        
        <div class="map-container">
          <iframe 
            title="Office Location"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d193595.25299748826!2d-74.11976389828391!3d40.69766374859258!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x89c24fa5d33f083b%3A0xc80b8f06e177fe62!2sNew%20York%2C%20NY%2C%20USA!5e0!3m2!1sen!2s!4v1644262070741!5m2!1sen!2s"
            width="100%"
            height="250"
            style="border:0;"
            allowfullscreen=""
            loading="lazy">
          </iframe>
        </div>
      </div>
      
      <div class="contact-form">
        <form on:submit={handleSubmit}>
          <div class="form-group">
            <input 
              type="text" 
              placeholder={content.contact.form.namePlaceholder}
              bind:value={formData.name}
              required
              class="form-input"
            />
          </div>
          
          <div class="form-row">
            <div class="form-group">
              <input 
                type="email" 
                placeholder={content.contact.form.emailPlaceholder}
                bind:value={formData.email}
                required
                class="form-input"
              />
            </div>
            
            <div class="form-group">
              <input 
                type="tel" 
                placeholder={content.contact.form.phonePlaceholder}
                bind:value={formData.phone}
                class="form-input"
              />
            </div>
          </div>
          
          <div class="form-group">
            <textarea 
              placeholder={content.contact.form.messagePlaceholder}
              bind:value={formData.message}
              required
              rows="6"
              class="form-input"
            ></textarea>
          </div>
          
          <button type="submit" class="btn btn-primary btn-submit">
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
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
  
  .info-card {
    display: flex;
    gap: 1rem;
    margin-bottom: 2rem;
  }
  
  .info-icon {
    flex-shrink: 0;
    width: 50px;
    height: 50px;
    background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
    border-radius: var(--radius-md);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }
  
  .info-card h4 {
    font-size: 1.125rem;
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 0.5rem;
  }
  
  .info-card p {
    color: var(--text-secondary);
  }
  
  .map-container {
    margin-top: 2rem;
    border-radius: var(--radius-lg);
    overflow: hidden;
    box-shadow: var(--shadow-md);
  }
  
  .contact-form {
    background: var(--bg-light);
    padding: 2.5rem;
    border-radius: var(--radius-lg);
  }
  
  .form-group {
    margin-bottom: 1.5rem;
  }
  
  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
  
  .form-input {
    width: 100%;
    padding: 0.875rem;
    border: 1px solid var(--border-color);
    border-radius: var(--radius-md);
    font-size: 1rem;
    transition: all 0.3s ease;
    background: white;
  }
  
  .form-input:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
  }
  
  textarea.form-input {
    resize: vertical;
    font-family: inherit;
  }
  
  .btn-submit {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
  }
  
  @media (max-width: 768px) {
    .contact-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    
    .form-row {
      grid-template-columns: 1fr;
    }
  }
</style>