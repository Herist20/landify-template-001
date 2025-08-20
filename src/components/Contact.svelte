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

<section id="contact" class="contact-section">
  <div class="contact-container">
    <h2 class="section-title">{content.contact.title}</h2>
    <p class="section-subtitle">{content.contact.subtitle}</p>
    
    <div class="contact-grid">
      <div class="contact-info">
        <div class="info-item">
          <div class="info-icon">
            <MapPin size={24} />
          </div>
          <div class="info-content">
            <h4 class="info-title">Visit Our Office</h4>
            <p class="info-text">{content.company.address}</p>
          </div>
        </div>
        
        <div class="info-item">
          <div class="info-icon">
            <Phone size={24} />
          </div>
          <div class="info-content">
            <h4 class="info-title">Call Us</h4>
            <p class="info-text">{content.company.phone}</p>
          </div>
        </div>
        
        <div class="info-item">
          <div class="info-icon">
            <Mail size={24} />
          </div>
          <div class="info-content">
            <h4 class="info-title">Email Us</h4>
            <p class="info-text">{content.company.email}</p>
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
      
      <div class="contact-form-container">
        <form on:submit={handleSubmit} class="contact-form">
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
            <input 
              type="email" 
              placeholder={content.contact.form.emailPlaceholder}
              bind:value={formData.email}
              required
              class="form-input"
            />
            
            <input 
              type="tel" 
              placeholder={content.contact.form.phonePlaceholder}
              bind:value={formData.phone}
              class="form-input"
            />
          </div>
          
          <div class="form-group">
            <textarea 
              placeholder={content.contact.form.messagePlaceholder}
              bind:value={formData.message}
              required
              rows="6"
              class="form-textarea"
            ></textarea>
          </div>
          
          <button type="submit" class="submit-btn">
            <Send size={20} />
            {content.contact.form.submitButton}
          </button>
        </form>
      </div>
    </div>
  </div>
</section>

<style>
  .contact-section {
    padding: 4rem 0;
    background-color: #f9fafb;
  }

  .contact-container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  .section-title {
    font-size: 2.25rem;
    font-weight: bold;
    text-align: center;
    color: #1f2937;
    margin-bottom: 0.5rem;
  }

  .section-subtitle {
    font-size: 1.125rem;
    color: #4b5563;
    text-align: center;
    margin-bottom: 3rem;
  }

  .contact-grid {
    display: grid;
    gap: 4rem;
  }

  @media (min-width: 1024px) {
    .contact-grid {
      grid-template-columns: 1fr 1fr;
    }
  }

  .info-item {
    display: flex;
    gap: 1rem;
    margin-bottom: 2rem;
  }

  .info-icon {
    flex-shrink: 0;
    width: 3rem;
    height: 3rem;
    background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
    border-radius: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }

  .info-title {
    font-size: 1.125rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.5rem;
  }

  .info-text {
    color: #4b5563;
  }

  .map-container {
    margin-top: 2rem;
    border-radius: 0.75rem;
    overflow: hidden;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  }

  .contact-form-container {
    background-color: white;
    padding: 2.5rem;
    border-radius: 0.75rem;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  }

  .form-group {
    margin-bottom: 1.5rem;
  }

  .form-row {
    display: grid;
    gap: 1rem;
    margin-bottom: 1.5rem;
  }

  @media (min-width: 768px) {
    .form-row {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .form-input {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
    border-radius: 0.5rem;
    font-size: 1rem;
    transition: all 0.2s ease;
  }

  .form-input:focus {
    outline: none;
    border-color: #2563eb;
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
  }

  .form-textarea {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
    border-radius: 0.5rem;
    font-size: 1rem;
    resize: vertical;
    transition: all 0.2s ease;
  }

  .form-textarea:focus {
    outline: none;
    border-color: #2563eb;
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
  }

  .submit-btn {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    background-color: #2563eb;
    color: white;
    border-radius: 0.5rem;
    font-weight: 600;
    border: none;
    cursor: pointer;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    transition: all 0.3s ease;
  }

  .submit-btn:hover {
    background-color: #1d4ed8;
    transform: translateY(-2px);
  }
</style>