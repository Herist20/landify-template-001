<script>
  import { Star, Quote } from 'lucide-svelte';
  export let content;
</script>

<section id="testimonials" class="py-16 bg-white">
  <div class="max-w-7xl mx-auto px-4">
    <h2 class="text-4xl font-bold text-center text-gray-800 mb-2">{content.testimonials.title}</h2>
    <p class="text-lg text-gray-600 text-center mb-12">{content.testimonials.subtitle}</p>
    
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each content.testimonials.items as testimonial}
        <div class="bg-gray-50 p-8 rounded-xl relative hover:-translate-y-1 hover:shadow-xl transition-all duration-300">
          <div class="absolute top-6 right-6 text-blue-600 opacity-20">
            <Quote size={24} />
          </div>
          
          <div class="flex gap-1 text-yellow-400 mb-4">
            {#each Array(testimonial.rating) as _}
              <Star size={18} fill="currentColor" />
            {/each}
          </div>
          
          <p class="text-gray-600 leading-relaxed mb-6 italic">{testimonial.content}</p>
          
          <div class="flex items-center gap-4 pt-6 border-t border-gray-200">
            <img src={testimonial.image} alt={testimonial.name} class="w-12 h-12 rounded-full object-cover" />
            <div>
              <div class="font-semibold text-gray-800">{testimonial.name}</div>
              <div class="text-sm text-gray-600">{testimonial.role}</div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>