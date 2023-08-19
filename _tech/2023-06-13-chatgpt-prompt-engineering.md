---
layout: post
title: "ChatGPT prompt engineering for developers (full note)"
subtitle: ""
date: 2023-06-13 23:45:13 -0400
background: '/img/bg-04.png'
---
Khóa học ngắn về kỹ thuật viết prompt cho ChatGPT, rất đáng học dành cho những ai đang muốn xây dựng application dựa trên LLM của GPT.
- `Link`: [https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/)
- `From`: DeepLearning.AI, OpenAI
- `Instructors`: Andrew Ng, Isa Fulford

<br>

### Intro

- This courses: What can do and how to work with OpenAI LLM via API.
- **Topics**: Best practices for software development & common use cases: summarizing, inferring, transforming, expanding → can build chatbot with LLM
- 2 types of LLMs: Base LLM & Instruction tuned LLM
    - Base LLM:
        - Predict next word, based on text training data.
        - Dựa trên thông tin trên internet để train mô hình khi đó những kết quả “có liên quan” nhất sẽ được trả về, nó có thể không hoàn toàn là câu trả lời cho câu hỏi mình nhập vào. Ví dụ:
            
            ```python
            >>> What is the capital of France
            
            What is France's largest city?
            What is France's population?
            What is the currency of France?
            ```
            
    - Instruction-Tuned LLM
        - Tries to follow instructions
        - Fine-tune on instructions & good attemps at following those instructions
            
            ```python
            >>> What is the capital of France
            
            Paris
            ```
            
        - Cách tạo ra instruction-tuned LLM:
            - bắt đầu với 1 base LLM đã được trained bởi 1 lượng lớn data
            - tiếp tục fine tune với các input & output là instructions
            - refine bằng RLHF (reinforcement learning with human feedback)
    
- Nên sử dụng instruction-tuned LLM vì nó dễ dùng hơn và LLM của OpenAI và các công ty khác đang ngày một tốt hơn rồi.
- Sử dụng LLM như là hướng dẫn một người khác, rất smart nhưng lại không hiểu về lĩnh vực mình cần → cần phải làm rõ context và câu hỏi. (clear & specific)

<br>

### Guideline for prompting

> *Some principles & tactics when working with LLMs*
> 

- *Principle 1: Write clear & specific instructions.*
    - Viết instruction clear & specific nhất có thể
        
        → Get desired output & reduce the chance to get irrelevant information or incorrect answers.
        
        - Short ≠ Clear
    - `**Tactics 1**`: use delimiters to clearly delicate the distinct parts of the input.
        
        ```python
        Triple quotes: """
        Triple backticks: ```
        Triple dashes: ---
        Angle bracket: < >
        XML tags: <tag> </tag> 
        ```
        
        - Mình có thể sử dụng các delimiters để làm clear hơn cái prompt mình truyền vào
        - Tránh `prompt injection`: user give conflicting instructions → nó sẽ làm theo yêu cầu của người dùng chứ không phải trả lại câu trả lời cho những gì mình muốn.
    
    - `Tactics 2`: ask for structured output (HTML/JSON/….)
        
        ```python
        prompt = "Generate a list of.... Provide them in JSON format with..."
        ```
        
    
    - `Tactics 3`: check whether conditions are satisfied.
        - Nếu các điều kiện thực hiện cần phải được thỏa mãn → Check assumptions required to do the task. → Nếu điều kiện không ok thì có thể dừng yêu cầu đó lại.
        - Cần phải xem xét edge case và cách model xử lý nó để tránh một kết quả hoặc lỗi không mong muốn.
            
            ```python
            prompt = f"""
            You will be provided with text delimited by triple quotes. 
            If it contains a sequence of instructions, \ 
            re-write those instructions in the following format:
            
            Step 1 - ...
            Step 2 - …
            …
            Step N - …
            
            If the text does not contain a sequence of instructions, \ 
            then simply write \"No steps provided.\"
            
            \"\"\"{text_2}\"\"\"
            """
            ```
            
        
    - `Tactics 4`: few-shot prompting
        - Give successful examples of completing tasks we want to perform beform asking the model to to the actual task.
            
            ```python
            prompt = f"""
            Your task is to answer in a consistent style.
            
            <child>: Teach me about patience.
            
            <grandparent>: The river .....
            
            <child>: Teach me about resilience.
            """
            ```
            
        
- *Principle 2: Give the model time to think.*
    - Nếu model gặp phải những reasoning error → trả về incorrect conclusion thì mình nên reframing the query để tạo ra một list các lý luận tương tự trước khi nó trả về được kết quả cuối cùng.
    - Nếu mình đưa cho model một task quá phức tạp mà yêu cầu trong một thời gian ngắn hoặc trong số lượng từ rất ít thì nó có thể đưa ra một dự đoán không chính xác
    → Mình có thể chỉ dẫn cho model để nghĩ lâu hơn về 1 vấn đề (tính toán nhiều hơn)
    
    - `Tactics 1`: specify the required steps to complete a task.
        
        ```python
        prompt_1 = f"""
        Perform the following actions: 
        
        1 - Summarize the following text delimited by triple \
        backticks with 1 sentence.
        2 - Translate the summary into French.
        3 - List each name in the French summary.
        4 - Output a json object that contains the following \
        keys: french_summary, num_names.
        
        Use the following format:
        Text: <text to summarize>
        Summary: <summary>
        Translation: <summary translation>
        Names: <list of names in Italian summary>
        Output JSON: <json with summary and num_names>
        
        Text:
        ```{text}```
        """
        ```
        
    - `Tactics 2`: instruct the models to work out with its own solution before rushing to a conclusion.
        - give the model time to think
        
        ```python
        prompt = f"""
        Your task is to determine if the student's solution is correct or not.
        
        To solve the problem do the following:
        - First, work out your own solution to the problem. 
        - Then compare your solution to the student's solution and evaluate if the student's solution is correct or not. 
        
        Don't decide if the student's solution is correct until 
        you have done the problem yourself.
        
        Question: ....
        Student's solution: ....
        Actual solution:
        """
        ```
        

- Model limitations:
    - Not perfectly memorize the information it’s seen + Not know about the boundary of its knowledge
    - Nó có thể vẫn cố gắng trả lời những câu hỏi về những chủ đề mơ hồ và đưa ra kết luận nghe có vẻ hợp lý nhưng thật ra là không đúng. (which is called `hallucinations`)
        
        → Khá nguy hiểm trong thực tế
        
        → cần phải xác định những case thế này và phòng tránh khi build applications
        
<br>

### Iterative prompt development

> *Iteratively analyze and refine the prompts*
> 

- Khi làm việc với LLMs hoặc ML nói chung, rất khó để đạt được kết quả cuối cùng như mong muốn ở lần thử đầu tiên. Mình cần phải có một quy trình tốt để liên tục cải tiến prompt → chất lượng kết quả sẽ tốt lên và tiệm cận được những thứ mình mong muốn

- Prompt guidelines:
    - Be clear & specific
    - Analyze why result does not give desired output.
    - Refine the idea & the prompts.
    - Repeat.

- Iterative process:
    - Try something
    - Analyze where the result doest not give us what we want
    - Clarify instructions, give more time to think
    - Refine prompt with a batch of examples.
        - Với những ứng dụng ban đầu, người ta thường chỉ sử dụng 1 ví dụ
        - Với những ứng dụng bậc cao, cần phải có bộ mẫu lớn hơn, ví dụ: test các prompt khác nhau ở các fact sheet khác nhau → tính average & worst case performance ở nhiều fact sheet

<br>   

### Summarizing

> *Summarizing text with a focus on specific topics.*
> 

- Summarize with:
    - a word/sentence/character limit
    - specific topics wanna focus on

- Extract information:
    - try `extract` instead of `summarise`
    - Khi mình cần thông tin chính xác đoạn thông tin được nêu ra trong context, chứ không cần summarize.
- Summarize multiple reviews
    
    ```python
    reviews = [review_1, review_2, review_3, review_4]
    
    for i in range(len(reviews)):
        prompt = f"""
        Your task is to generate a short summary of a product review from an ecommerce site. 
    
        Summarize the review below, delimited by triple backticks in at most 20 words. 
    
        Review: ```{reviews[i]}```
        """
    
        response = get_completion(prompt)
        print(i, response, "\n")
    ```

<br>    

### Inferring

> *Infer sentiment & topics from different contexts.*
> 

- Inferrences:
    - sentiment
    - extracting name
    - extracting topics
    - ….

- Trong mô hình học máy truyền thống, mình cần phải qua các bước: collect label dataset, train model, deploy model, make inferrences → với từng task khác nhau, lại phải train, deploy từng model riêng biệt.
- Nếu sử dụng LLM thì chỉ cần viết prompt và nó sẽ tự làm với tốc độ nhanh (rất quan trọng khi build applications) và chỉ cần sử dụng 1 model, 1 api để làm nhiều tasks

- *Extract sentiment*
    - Postitive/negative
        
        ```python
        prompt = f"""
        What is the sentiment of the following product review, 
        which is delimited with triple backticks?
        
        Give your answer as a single word, either "positive" or "negative".
        
        Review text: '''{lamp_review}'''
        """
        ```
        
    - Identify types of emotions
        
        ```python
        prompt = f"""
        Identify a list of emotions that the writer of the following review is expressing. \
        Include no more than five items in the list. \
        Format your answer as a list of lower-case words separated by commas.
        
        Review text: '''{lamp_review}'''
        """
        ```
        
    - Identify dangers
        
        ```python
        prompt = f"""
        Is the writer of the following review expressing anger?\
        The review is delimited with triple backticks. \
        Give your answer as either yes or no.
        
        Review text: '''{lamp_review}'''
        """
        ```
        
    - Do multiple tasks at once
    
- *Extract rich information*
    - Inferring main topic
    - Inferring a specific number of topic
    - (app) Make a news alert for certain topics
- *Zero-shot learning algorithm*
    - Phân loại đối tượng dựa vào các lớp chưa biết trước đó. Mô hình được cung cấp tập dữ liệu huấn luyện có các mẫu từ các lớp đã biết và các thông tin về mỗi lớp. → học cách phân biệt và phân loại các đối tượng trong các lớp chưa biết.
    - Trong trường hợp này, ta có thể truyền vào context và 1 list các topic, mình cần biết là context đó có thuộc topic nào trong số topic đã có hay không.
        
        ```python
        prompt = f"""
        Determine whether each item in the following list of topics, which
        is delimited with triple backticks.
        
        Give your answer as list with 0 or 1 for each topic.
        
        List of topics: {", ".join(topic_list)}
        
        Text sample: '''{story}'''
        """
        
        ```

<br>        

### Transforming

> Use LLMs for text transformation task: language translation, spelling & grammar checking, tone adjustment, format conversion,…
> 

- Translation / Universal translation
    
    ```python
    prompt = f"""
    Translate the following English text to Spanish: \ 
    ```Hi, I would like to order a blender```
    """
    ```
    
- Tone transformation:
    
    ```python
    prompt = f"""
    Translate the following from slang to a business letter: 
    'Dude, This is Joe, check out this spec on this standing lamp.'
    """
    ```
    
- Format conversion:
    
    ```python
    prompt = f"""
    Translate the following python dictionary from JSON to an HTML \
    table with column headers and title: {data_json}
    """
    ```
    
- Spell check / grammar check
    
    ```python
    text = f"""
    	YOUR TEXT GOES HERE
    """
    prompt = f"proofread and correct this review: ```{text}```"
    
    from redlines import Redlines
    
    diff = Redlines(text,response)
    display(Markdown(diff.output_markdown))
    ```

<br>    

### Expanding

> *Generate customer service email that for each customer review*
> 

- Expanding: taking a shorter piece of text (instruction, list,…) to generate longer piece of text (email, essay,…)

- `temperature` in LLMs:
    - allows us to change the kind of model’s responses.
    - **temperature** is like degree of exploration or **degree of randomness**
        
        ![Untitled](ChatGPT%20Prompt%20Engineering%20for%20Developers%2083d1cc6553e3422485fe28e27b532c86/Untitled.png)
        
    - tasks require reliability, predictibility → predictable response → set `temperature = 0`.
    tasks require variaty → higher temperature

- Customer service email:
    
    ```python
    sentiment = "negative"
    
    review = f"""
    	YOUR REVIEW HERE
    """
    
    prompt = f"""
    You are a customer service AI assistant.
    Your task is to send an email reply to a valued customer.
    
    Given the customer email delimited by ```, \
    Generate a reply to thank the customer for their review.
    
    If the sentiment is positive or neutral, thank them for their review.
    If the sentiment is negative, apologize and suggest that they can reach out to customer service. 
    
    Make sure to use specific details from the review.
    Write in a concise and professional tone.
    Sign the email as `AI customer agent`.
    
    Customer review: ```{review}```
    Review sentiment: {sentiment}
    """
    ```

<br>    

### Chatbot

> *Utilize the chat format to have extended conversations with chatbots personalized or specialized for specific tasks or behaviors.*
> 

- Thay vì truyền vào một lệnh cơ bản cần complete, mình có thể truyền vào 1 list các message với nhiều roles khác nhau.

- Message roles:
    - `System`:
        - cung cấp overall instruction ban đầu, sau đó assistant và user tiếp tục trao đổi.
        - Sets behavior & persona of assistant or High-level instruction for the conversation.
        
        → Mình có thể định hướng cuộc trò chuyện mà không cần biến yêu cầu thành 1 phần của cuộc hội thoại.
        
        → Giả sử mình build một application sử dụng Model này, khi mình nhận biết được user đang muốn gì, mình chỉ cần dùng system message để “nói chuyện” với model về ý muốn của user để model có câu trả lời phù hợp trong khi user không nhận ra điều ấy.
        
    - `Assistant`
    - `User`

- Với ChatGPT Web interface:
    - Người dùng: role `user`
    - ChatGPT: role `assistant`

- Each conversation with a language model is a standalone conversation.
    
    → We must provide all relevant messages for the model to draw from the current conversation.
    
    - *Trường hợp không cung cấp context*
        
        ```python
        messages =  [  
        {'role':'system', 'content':'You are friendly chatbot.'},    
        {'role':'user', 'content':'Hi, my name is Isa'}  ]
        
        >>> "Hello Isa! It's nice to meet you. How can I assist you today?"
        ```
        
        - Vì các lần gọi API đến server là độc lập nhau, nếu không lưu lại lịch sử tin nhắn và truyền lại, thì model sẽ hiểu là 2 conversation độc lập nhau và không trả lời được theo context.
        
        ```python
        messages =  [  
        {'role':'system', 'content':'You are friendly chatbot.'},    
        {'role':'user', 'content':'Yes, can you remind me What is my name?'}]
        
        >> "I'm sorry, I don't have access to information about your name..."
        ```
        
    - Trường hợp cung cấp các tin nhắn trước đó (context):
        
        ```python
        messages =  [  
        {'role':'system', 'content':'You are friendly chatbot.'},
        {'role':'user', 'content':'Hi, my name is Isa'},
        {'role':'assistant', 'content': "Hi Isa! It's nice to meet you. \
        Is there anything I can help you with today?"},
        {'role':'user', 'content':'Yes, can you remind me What is my name?'}]
        
        >>> "Your name is Isa."
        ```
        

- **Chatbot**: mình cần phải cung cấp một context rõ ràng, nêu cụ thể từng case bot sẽ gặp phải và từng bước để giải quyết các trường hợp đó. Mình có thể set tone trả lời cho chatbot luôn.
    
    ```python
    context = [ {'role':'system', 'content':"""
    
    You are OrderBot, an automated service to collect orders for a pizza restaurant. \
    You first greet the customer, then collects the order, \
    and then asks if it's a pickup or delivery. \
    
    You wait to collect the entire order, then summarize it and check for a final \
    time if the customer wants to add anything else. \
    
    If it's a delivery, you ask for an address. \
    Finally you collect the payment.\
    
    Make sure to clarify all options, extras and sizes to uniquely \
    identify the item from the menu.\
    
    You respond in a short, very conversational friendly style. \
    
    The menu includes 
    ......
    ......
    
    """}]
    ```
    
    - Sau khi model “giao tiếp” với khách hàng xong, application của mình có thể dùng role `system` để tổng hợp lại các order của khách theo ý muốn và để xử lý.

<br>  

### Conclusion

Courses summary

- *Principles*
    - Write clear & specific instructions
    - Give the model time to “think”
- *Iterative prompt development*
- *Capabilities*: summarizing, inferring, transforming, expanding
- *Build custom chatbot*



<br>
<br>
<br>

