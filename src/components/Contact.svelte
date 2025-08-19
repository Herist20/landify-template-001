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

<section id="contact" class="py-16 bg-gray-50">
  <div class="max-w-7xl mx-auto px-4">
    <h2 class="text-4xl font-bold text-center text-gray-800 mb-2">{content.contact.title}</h2>
    <p class="text-lg text-gray-600 text-center mb-12">{content.contact.subtitle}</p>
    
    <div class="grid lg:grid-cols-2 gap-16">
      <div>
        <div class="flex gap-4 mb-8">
          <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-blue-600 to-blue-700 rounded-lg flex items-center justify-center text-white">
            <MapPin size={24} />
          </div>
          <div>
            <h4 class="text-lg font-semibold text-gray-800 mb-2">Visit Our Office</h4>
            <p class="text-gray-600">{content.company.address}</p>
          </div>
        </div>
        
        <div class="flex gap-4 mb-8">
          <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-blue-600 to-blue-700 rounded-lg flex items-center justify-center text-white">
            <Phone size={24} />
          </div>
          <div>
            <h4 class="text-lg font-semibold text-gray-800 mb-2">Call Us</h4>
            <p class="text-gray-600">{content.company.phone}</p>
          </div>
        </div>
        
        <div class="flex gap-4 mb-8">
          <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-blue-600 to-blue-700 rounded-lg flex items-center justify-center text-white">
            <Mail size={24} />
          </div>
          <div>
            <h4 class="text-lg font-semibold text-gray-800 mb-2">Email Us</h4>
            <p class="text-gray-600">{content.company.email}</p>
          </div>
        </div>
        
        <div class="mt-8 rounded-xl overflow-hidden shadow-md">
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
      
      <div class="bg-white p-10 rounded-xl shadow-lg">
        <form on:submit={handleSubmit}>
          <div class="mb-6">
            <input 
              type="text" 
              placeholder={content.contact.form.namePlaceholder}
              bind:value={formData.name}
              required
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-600 focus:ring-2 focus:ring-blue-100 transition-all"
            />
          </div>
          
          <div class="grid md:grid-cols-2 gap-4 mb-6">
            <input 
              type="email" 
              placeholder={content.contact.form.emailPlaceholder}
              bind:value={formData.email}
              required
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-600 focus:ring-2 focus:ring-blue-100 transition-all"
            />
            
            <input 
              type="tel" 
              placeholder={content.contact.form.phonePlaceholder}
              bind:value={formData.phone}
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-600 focus:ring-2 focus:ring-blue-100 transition-all"
            />
          </div>
          
          <div class="mb-6">
            <textarea 
              placeholder={content.contact.form.messagePlaceholder}
              bind:value={formData.message}
              required
              rows="6"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-600 focus:ring-2 focus:ring-blue-100 transition-all resize-y"
            ></textarea>
          </div>
          
          <button type="submit" class="w-full flex items-center justify-center gap-2 px-6 py-3 bg-blue-600 text-white rounded-lg font-semibold hover:bg-blue-700 transform hover:-translate-y-0.5 transition-all duration-300 shadow-lg">
            <Send size={20} />
            {content.contact.form.submitButton}
          </button>
        </form>
      </div>
    </div>
  </div>
</section>