# Lab-Final-Q2-

@code {
    [Parameter]
    public string QuestionText { get; set; }

    [Parameter]
    public string[] Options { get; set; }

    [Parameter]
    public string DifficultyLevel { get; set; }
}

<div class="question-card">
    <h3>@QuestionText</h3>
    <ul>
        @foreach (var option in Options)
        {
            <li>@option</li>
        }
    </ul>
    <p><strong>Difficulty Level:</strong> @DifficultyLevel</p>
</div>




@code {
    // A list of quiz questions to display
    [Parameter]
    public List<Question> Questions { get; set; }
}

<div class="question-list">
    @foreach (var question in Questions)
    {
        <QuestionCard 
            QuestionText="@question.QuestionText"
            Options="@question.Options"
            DifficultyLevel="@question.DifficultyLevel" />
    }
</div>




@page "/quiz"

@code {
    // Sample quiz questions
    private List<Question> sampleQuestions = new List<Question>
    {
        new Question
        {
            QuestionText = "What is the capital of France?",
            Options = new[] { "Paris", "London", "Berlin", "Madrid" },
            DifficultyLevel = "Easy"
        },
        new Question
        {
            QuestionText = "Which planet is known as the Red Planet?",
            Options = new[] { "Earth", "Mars", "Jupiter", "Saturn" },
            DifficultyLevel = "Medium"
        }
    };
}

<h2>Quiz Questions</h2>
<QuestionList Questions="@sampleQuestions" />




.question-card {
    border: 1px solid #ccc;
    padding: 15px;
    margin-bottom: 10px;
    border-radius: 5px;
    background-color: #f9f9f9;
}

.question-list {
    display: flex;
    flex-direction: column;
}

h3 {
    font-size: 18px;
}

ul {
    list-style-type: none;
    padding: 0;
}



